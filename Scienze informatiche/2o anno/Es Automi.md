$L_{1}=\{w\in\{0,1\}^{*}|w$ contiene un numero di 0 multiplo di 3}

|       | 1   | 0   |
| -----:| --- | --- |
| -> q0 | q0  | q1  |
|    q1 | q1  | q2  |
|  * q2 | q2  | q0  |

$L_{2}=\{w\in\{0,1\}^{*}|w$ è la codifica binaria di un numero multiplo di 3}

|       | 1   | 0   |
| ----: | --- | --- |
| -> s0 | s1  | s3  |
|    s1 | s3  | s2  |
|    s2 | s2  | s1  |
|  * s3 | s2  | s3  |
$L_{1}-\{w\in\{0,1\}^{*}|w$ contiene un numero di 0 multiplo di 3 e w è codifica binaria di un numero multiplo di 3}

|          | 0   | 1   |
| -------- | --- | --- |
| (q0, s0) | ()  |     |
| (q0, s1) |     |     |
| (q0, s2) |     |     |
