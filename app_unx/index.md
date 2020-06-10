
## Configuration Option

_____
| **Source Coding** |         None        |  2-nary Manchester |
| ----------------- | ------------------- | ------------------ |
|	       None       | :white_check_mark:  | :white_check_mark: | 
|        2to1       | :white_check_mark:  |       :x:          |
|        3to1       | :white_check_mark:  |       :x:          |
|        4to1       | :white_check_mark:  |       :x:          |
|        5to1       | :white_check_mark:  |       :x:          |
Possible (source coding / line coding) combinations for thermal covert channel experiments.
_____
|       **Line Coding**       |       **pwm**      |    **rect**        |     **rect_vm**    |
| --------------------------- | ------------------ | ------------------ | ------------------ |
| None (all source codings)   | :white_check_mark: |         :x:        |         :x:        |
| None (source coding "None") |         :x:        | :white_check_mark: | :white_check_mark: |
| 2-nary Manchester           | :white_check_mark: | :white_check_mark: | :white_check_mark: |
Possible (line coding / signaltype) combinations for thermal covert channel experiments.
_____
| **Source Coding** |       **None**     | **RZ\_govcons\_cmd\_sec** |
| ----------------- | ------------------ | ------------------------- |
|	       None       | :white_check_mark: |    :white_check_mark:     | 
|        2to1       | :white_check_mark: |            :x:            |
|        3to1       | :white_check_mark: |            :x:            |
|        4to1       | :white_check_mark: |            :x:            |
|        5to1       | :white_check_mark: |            :x:            |
Possible (source coding / line coding) combinations for frequency covert channel experiments.
_____
|    **Line Coding**    |        **cmd**     |       **util**     |
| --------------------- | ------------------ | ------------------ |
| RZ\_govcons\_cmd\_sec | :white_check_mark: |         :x:        |
Possible (line coding / signaltype) combinations for frequency covert channel experiments.
_____
|   **Signaltype**  | **freq-cc\_conservative** |   **loadgen\_bc**  |   **loadgen\_mt**  |  **loadgen\_pwm**  |   **loadgen\_st**  |
| ----------------- | ------------------------- | ------------------ | ------------------ | ------------------ | ------------------ |
| frequency cmd     |    :white_check_mark:     |         :x:        |         :x:        |         :x:        |         :x:        |
| frequency util    |    :white_check_mark:     |         :x:        |         :x:        |         :x:        |         :x:        |
| thermal pwm       |            :x:            |         :x:        |         :x:        | :white_check_mark: |         :x:        |
| thermal rect      |            :x:            | :white_check_mark: | :white_check_mark: |         :x:        | :white_check_mark: |
| thermal rect\_vm  |            :x:            |         :x:        |         :x:        |         :x:        |         :x:        |
Possible (signaltype / source application) combinations.
_____
|   **SNK Applications**  |     **thermal**    |   **thermal\_vm**  |    **frequency**   |      **power**     |
| ----------------------- | ------------------ | ------------------ | ------------------ | ------------------ |
| *meter\_thermal\_adb*   | :white_check_mark: |          :x:       |         :x:        |         :x:        | 
| *meter\_freq\_cpuinfo*  |         :x:        |          :x:       | :white_check_mark: |         :x:        | 
| *meter\_freq\_freqinfo* |         :x:        |          :x:       | :white_check_mark: |         :x:        | 
| *meter\_freq\_sysfs*    |         :x:        |          :x:       | :white_check_mark: |         :x:        | 
| *meter\_freq\_sysfsdbg* |         :x:        |          :x:       | :white_check_mark: |         :x:        | 
| *meter\_power*          |         :x:        |          :x:       |         :x:        | :white_check_mark: |
| *meter\_thermal*        | :white_check_mark: |          :x:       |         :x:        |         :x:        |
Possible (sink application / attack media) combinations.
_____

____
[Back to Home](/home)

[One Level Up](/executing-experiments/general)
