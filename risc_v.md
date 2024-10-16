## Bezug zur Aufgabenstellung
Es soll Folgendes realisiert werden:
- Base Instruction Set für 64 Bit ohne compressed (*C*) Instruktionen
- 64-Bit Adressen -> 64 Register

## RISC-V Instruction Set
Unterteilung in:
- das Base Integer Instruction Set und
- ein Set an optionalen Extensions (M, A, F, ...)
### Base Integer Instruction Set
- auch bezeichnet als "**RV32I**" bzw. "**RV64I**"
- für general-purpose computing
### Instruktionsformate

| Typ    | Beschreibung                                  |
| ------ | --------------------------------------------- |
| R-type | **register-to-register**                      |
| I-type | Operationen mit **Immediate** (12 Bit)        |
| S-type | **Store**-Operationen (reg -> mem)            |
| B-type | **bedingte** Sprünge                          |
| U-type | Operationen mit **großer Immediate** (20 Bit) |
| J-type | **unbedingte** Sprünge                        |
## RISC-V Register File
- bezeichnet die in Menge der in RISC-V benutzten Register
- **Unterteilung** in:
	- Integer Registers
	- Floating-Point Registers (nur vorhanden für implementierte F- oder D-Extension)
### Integer Registers
- 32 Stck. in 32-Bit, 32 Bit breit
- 32 oder 64 Stck. in 64-Bit (je nach Größe des Address Spaces), 64 Bit breit
- Inhalt - Werte im Format ...
	- Boolean
	- 2er-Komplement (signed)
	- unsigned Integer
#### Naming Convention für Integer Register
- x0 als Spezialfall
- x1-x31 als General-Purpose Register, manche mit speziellem Namen zur Zuordnung ihres Zwecks

| Name            | Semantischer Name | Zweck                                                 |
| --------------- | ----------------- | ----------------------------------------------------- |
| x0              | -                 | hardwired zu `0`                                      |
| x1              | ra                | **return** Adresse für Funktionsaufrufe               |
| x2              | sp                | **Stack** Pointer                                     |
| x3              | gp                | **Global** Pointer (global data)                      |
| x4              | tp                | **Thread** Pointer (thread-lokaler Speicher)          |
| x5-x11          | t0-t6             | **temporäre** Register                                |
| x10-x17         | a0-a7             | Register für **Funktionsargumente**                   |
| x8, x9, x18-x27 | s0-s11            | "Saved" Register für Werte zwischen Funktionsaufrufen |
| x28-x31         | t3-t6             | weitere **temporäre** Register                        |
## Privileged Instruktionen
- *unprivileged* Instruktionen: können von jeder auf dem Prozessor laufenden Software ausgeführt werden, greifen auf keine sensiblen System-Ressourcen zu
- *privileged* Instruktionen: sollen nur vom OS oder Kernel ausgeführt werden, zum Verwalten von System-Ressourcen, auch zum Verwalten externer Geräte
