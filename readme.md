# BTR to decimal number

Write a program that translate a number written in a BTR format to its decimal representation.


ANSWER:


(define btd-val &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;; valore: [-1, 0, 1]<br/>
&emsp;(lambda (btd) &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; ; d: carattere -/./+<br/>
&emsp;&emsp;(cond ((char=? btd #\-) -1)<br/>
&emsp;&emsp;&emsp;&emsp;   ((char=? btd #\.)  0)<br/>
&emsp;&emsp;&emsp;&emsp;   ((char=? btd #\+) +1)<br/>
&emsp;&emsp;&emsp;&emsp;   )<br/>
&emsp;&emsp;))<br/>

(define btr-val &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;; valore: intero<br/>
&emsp;(lambda (btr) &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;  ; btr: stringa non vuota di -/./+<br/>
&emsp;&emsp;(let ((k (- (string-length btr) 1))<br/>
&emsp;&emsp;&emsp;&emsp; )<br/>
&emsp;&emsp;&emsp;(let ((pre (substring btr 0 k)) &emsp;&emsp;; pre = prefix<br/>
&emsp;&emsp;&emsp;&emsp;&emsp;(lsd (string-ref btr k)) &emsp;&emsp;&emsp;; lsd = least significant digit<br/>
&emsp;&emsp;&emsp;&emsp;&emsp;)  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; ; per facilitare la leggibilita'<br/>
&emsp;&emsp;&emsp;&emsp;(if (= k 0)<br/>
&emsp;&emsp;&emsp;&emsp;&emsp; (btd-val lsd)<br/>
&emsp;&emsp;&emsp;&emsp;&emsp; (+ (* 3 (btr-val pre)) (btd-val lsd))<br/>
&emsp;&emsp;&emsp;&emsp;&emsp; )))<br/>
&emsp;&emsp;))<br/>

(btr-val "+-.+"); → 19