# Design Calculations

Complete design calculations for the 24V to 5V, 2A Buck Converter.

## 1. Duty Cycle Calculation

Theoretical duty cycle for an ideal Buck converter:

D = Vout / Vin = 5 / 24 = 0.2083 (20.83%)

However, considering conduction losses (MOSFET Rds(on), diode Vf), 
the practical duty cycle is slightly higher:

D_practical ≈ 22.1%

## 2. Inductor Selection

Target inductor current ripple: 30% of Iout

ΔIL = 0.3 × Iout = 0.3 × 2 = 0.6 A

L = (Vin - Vout) × D / (ΔIL × fsw)
L = (24 - 5) × 0.22 / (0.6 × 100000)
L = 69.7 µH

Selected value: 100 µH (standard value, provides lower ripple)

## 3. Output Capacitor Selection

Target output voltage ripple: 50 mV (1% of Vout)

C = (Vout × (1-D)) / (8 × L × ΔVout × fsw²)
C = 97.5 µF

Selected value: 100 µF (standard value)

## 4. MOSFET Selection

Requirements:
- Vds_max ≥ Vin × 1.5 = 36V (with safety margin)
- Id_max ≥ Iout × 1.5 = 3A (with safety margin)
- Low Rds(on) for efficiency

Selected: IRF540N (100V, 33A, Rds(on) = 44 mΩ)

## 5. Diode Selection

Requirements:
- Vr ≥ Vin × 1.5 = 36V
- If ≥ Iout × 1.5 = 3A
- Schottky for low forward voltage

Selected: MBRS340 (40V, 3A, Vf = 0.5V)

## 6. Expected Performance

| Parameter | Value |
|---|---|
| Vout | 5.00 V |
| Iout | 2.00 A |
| ΔIL | 0.418 A |
| ΔVout (ripple) | ~5.2 mV |
| Duty Cycle | 22.1% |
