java c
„Numerische Methoden II“
Wintersemester 2024/2025
Aufgabe 4 – Lineare Gleichungssysteme und iterative Solver


Für das erfolgreiche Bestehen von Assignment 4 müssen lauffähige Programme, sowie ein kurzer Report zu den Aufgaben abgegeben werden.
Es sollen verschiedene Verfahren zur Lösung von linearen Gleichungssystemen untersucht werden. Die Lösungsroutinen aus der Eigen-Bibliothek werden hierbei an einem Wärmeleitproblem angewendet und in C++ programmiert.
Aufgabenstellung
In dieser Aufgabe wird eine quadratische Metallplatte mit der Länge L = 1 betrachtet, die mithilfe einer Induktionsspule homogen beheizt wird. Aufgrund der geringen Dicke der Platte kann die Berechnung zweidimensional erfolgen. Die Temperatur am Rand der Metallplatte kann als konstant angenommen werden.

Abbildung 1: Zweidimensionale Modellierung einer induktiv beheizten Metallplatte
Das Problem wird stationär betrachtet, sodass es mit der Poisson-Gleichung beschrieben werden kann:

Wobei u die Temperatur und f der flächenspezifische Wärmeeintrag ist. Am Rand der Platte wird eine konstante Temperatur angenommen, sodass Dirichlet-Randbedingungen definiert werden können:

Zur Diskretisierung kann das finite Differenzenverfahren verwendet werden, mit einer konstanten Schrittweite h = 1/n, wobei n die Anzahl der Schritte in x- und y-Richtung angibt. Das diskrete Problem für die Poisson-Gleichung ist ein lineares Gleichungssystem welches ohne Randpunkte folgende Anordnung besitzt:

Es gilt hierbei:

dabei ist T ∈ R{n−1×n−1} und I die (n − 1) × (n − 1) Einheitsmatrix.
Für den Rand werden Dirichlet-Randbedingungen verwenden, sodass für die rechte Seite gilt:

Wobei 2 ≤ j ≤ n − 2 gilt.
Für die Nummerierung der Gitterpunkte wurde dabei eine Standardanordnung verwendet (siehe Einführungsveranstaltung).
Hinweis:
• Für diese Aufgabe werden Funktionen aus der Eigen-Bibliothek verwendet (siehe Einführungsveranstaltung)
Aufgabe 2.1.
Folgendes lineares Gleichungssystem (LGS) A x = b ist gegeben. Zur Lösung eines solchen LGS kann die Matrix als dense oder als sparse Matrix-Typ betrachtet werden.

Um dünnbesetzte Matrizen als sparse Matrix-Typ abzuspeichern kann das Compressed Row Storage (CRS) Verfahren verwendet werden. Hierbei werden nur die von Null unterschiedlichen Einträge der Matrix abg代 写Numerische Methoden II Wintersemester 2024/2025 Aufgabe 4 – Lineare Gleichungssysteme und iterative SolverC/C++
代做程序编程语言espeichert. Dies geschieht in Form. eines Arrays val, wobei die Informationen der abgespeicherten Werte in zwei weiteren Arrays ir und ic abgespeichert werden (siehe Einführungsveranstaltung).
1. Führen Sie das CRS-Verfahren für die Matrix A händisch durch.
2. Erstellen Sie ein Programm zur Lösung von LGS, bei der das direkte LU-Verfahren mit einer dense/sparse Matrix verwendet wird. Das Programm soll folgende Funktionen beinhalten:
a. Einlesen der Daten aus einer Datei
b. Auswahl und Abfrage des Matrix-Types (dense/sparse)
c. Lösung des LGS mit LU (aus der Eigen-Bibliothek)
d. Fehlerbehandlung
e. Ausgabe der Ergebnisse
Hinweis:
• Die Dokumentation für den LU-Solver von sparse Matrix-Typen befindet sich auf folgender Website (https://eigen.tuxfamily.org/dox/classEigen_1_1SparseLU.html )
Aufgabe 2.2.
1. Modifizieren Sie ihr Programm aus Aufgabe 2.1. so, dass Sie neben dem Testsystem ebenfalls die Matrix A und b zur Lösung des Wärmeleitproblems aufrufen können.
a. Erstellung der Poisson-Matrix A in Abhängigkeit der Anzahl der Schritte zwischen der Gitterpunkten n, des Wärmeeintrags f und der Werte am Rand g. ➔ n, f und g sollen aus einer Datei oder über die Konsole vorgegeben werden
b. Speicherung von Matrix A soll als sparse Matrix
c. Auswahl zwischen direkten Solver (LU) und iterativen Solver (konjugierte Gradienten)
d. Lösung des LGS mit ausgewählten Solver
e. Ausgabe der Ergebnisse
2. Vergleichen Sie die zur Lösung benötigten CPU-Zeiten und Iterationen des direkten und des iterativen Lösungsverfahrens für sparse besetzte Poisson-Matrizen mit der Schrittanzahl n =10, 25, 40, 60 miteinander. Stellen Sie hierfür die genannten Größen über die Schrittanzahl beider Solver dar.
Welche Unterschiede fallen auf und welche Gründe gibt es dafür?
Hinweise:
• Erstellen Sie zunächst die Blöcke T und I und belegen Sie damit die Matrix A
• Für die weiteren Aufgaben gilt f = 1 und g = 0
• Die Dokumentation für den konjugierte Gradienten-Solver von sparse Matrix-Typen befindet sich auf folgender Website
(https://eigen.tuxfamily.org/dox/classEigen_1_1ConjugateGradient.html )
Auswertung:
• Stellen Sie die Temperatur im Gebiet Ω in einem 3D-Plot dar. Verwenden Sie hierfür die Unterfunktion gnuplot_splot()









         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
