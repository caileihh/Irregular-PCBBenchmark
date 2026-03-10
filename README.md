# Irregular-PCB Benchmark

This repository provides an irregular printed circuit board (PCB) placement benchmark for research on PCB layout optimization.

The benchmark contains PCB layouts with irregular board boundaries, device geometries, pin shapes, and netlist connectivity, which can be used to evaluate algorithms for placement.

<!-- Repository:  
https://github.com/caileihh/Irregular-PCBBenchmark -->

---

# Dataset Structure

Each PCB instance is stored in an independent directory:



```
Irregular-PCBBenchmark/
├── case1/
│   ├── boundary.txt
│   ├── device_outlines.txt
│   ├── pins.txt
│   ├── netlist.txt
│   └── fig_1.png
├── case2/
│   └── ...
```


- `boundary.txt` : PCB irregular boundary polygon  
- `device_outlines.txt` : device geometric outlines  
- `pins.txt` : pin shapes for each device  
- `netlist.txt` : electrical connectivity between pins  
- `fig_x.png` : visualization of the PCB layout

---

# File Format Description

## 1. boundary.txt

Defines the **irregular PCB boundary polygon**.

Each line contains one vertex coordinate:
(x, y)



Notes:

- The vertices form a **closed polygon describing the PCB boundary**.
- Points are listed **in order along the boundary**.
- The first and last points implicitly form a closed loop.

---

## 2. device_outlines.txt

Defines the **geometric outline of each device**.

Each line corresponds to **one device**, represented by the vertex coordinates of its polygon:

[x1, y1, x2, y2, x3, y3, ..., xn, yn]


Notes:

- Coordinates represent the **device outline polygon**.
- Most devices are rectangles, and the format supports **arbitrary polygons**.
- Devices are indexed according to the **line order**.

---

## 3. pins.txt

Defines the **pin geometries for each device**.

Each line corresponds to **one device**, containing a list of pin polygons.

Format:


[
[x1, y1, x2, y2, x3, y3, x4, y4],
[x1, y1, x2, y2, x3, y3, x4, y4],
...
]



Notes:

- Each inner list represents **one pin polygon**.
- Pins are associated with devices according to **line index**.

---

## 4. netlist.txt

Defines the **net identifier associated with each pin of every device**.

Each line corresponds to **one device**, and each value represents the **net ID connected to the corresponding pin** defined in `pins.txt`.


Notes:

- Each integer represents a **net identifier** connected to the corresponding pin.
- The order of values **matches the pin order in `pins.txt` for the same device**.
- `0` denotes **GND (ground)**.
- Pins connected to GND (`0`) are **excluded from the HPWL (Half-Perimeter Wirelength) computation**.

---


# Example Visualization

Each case contains a visualization figure (`fig_x.png`) illustrating:

- PCB irregular boundary
- device placement
- pin locations

---