<h2>Crypt or Encode [CRYPTO 200]</h2>

>John Doe developed his own "cryptography" because he did not trust existing ones.<br>
>You can test John's "encryption" on {site}<br>
>The "encrypted" flag is: Zoim9tRgkNy+iGBmvrLeqr6MaGLY+g==<br>
>Your job is to show John that he should not try to create his own encryption, especially if he knows only conversions like base64 and ASCII x Decimal.<br>
>Send the flag like this 3DS{[0-9a-zA-Z-]+}<br>

<h3>EN / <a href="#rozwiazanie">PL</a></h3>

<h3>Solution:</h3>

The solution was surprisingly short.

The flag is encoded in `base64`.<br>
After decoding I wrote the values of the characters:

<pre>
>>> flag = 'Zoim9tRgkNy+iGBmvrLeqr6MaGLY+g=='
>>> 
>>> import base64
>>> list(base64.b64decode(flag))
[102, 136, 166, 246, 212, 96, 144, 220, 190, 136, 96, 102, 190, 178, 222, 170, 190, 140, 104, 98, 216, 250]
</pre>

You can see that the values are a bit big.<br>
It is known that the beginning of the flag is `3DS{`.<br>
Values of these chars are:

<pre>
>>> list(ord(i) for i in '3DS{')
[51, 68, 83, 123]
</pre>

That's half the size.<br>
So it was enough to reduce the value of all chars by half.

<pre>
>>> flag = 'Zoim9tRgkNy+iGBmvrLeqr6MaGLY+g=='
>>> flag = list(base64.b64decode(flag))
>>> ''.join(chr(int(int(i)/2)) for i in flag)
'3DS{j0Hn_D03_YoU_F41l}'
</pre>

<h3>[EN](#solution) / PL</h3>

<h3>Rozwiązanie:</h3>

Rozwiązanie było zaskakująco krótkie.

Flaga jest zakodowana w `base64`.<br>
Po rozkodowaniu wypisałem wartości poszczególnych znaków:

<pre>
>>> flag = 'Zoim9tRgkNy+iGBmvrLeqr6MaGLY+g=='
>>> 
>>> import base64
>>> list(base64.b64decode(flag))
[102, 136, 166, 246, 212, 96, 144, 220, 190, 136, 96, 102, 190, 178, 222, 170, 190, 140, 104, 98, 216, 250]
</pre>

Widać, że wartości są trochę duże.<br>
Wiadomo, że początek flagi, to `3DS{`.<br>
Wartości tych znaków, to:

<pre>
>>> list(ord(i) for i in '3DS{')
[51, 68, 83, 123]
</pre>

Czyli o połowę mniejsze.<br>
Wystarczyło zatem zmniejszyć wartości wszystkich znaków o połowę.

<pre>
>>> flag = 'Zoim9tRgkNy+iGBmvrLeqr6MaGLY+g=='
>>> flag = list(base64.b64decode(flag))
>>> ''.join(chr(int(int(i)/2)) for i in flag)
'3DS{j0Hn_D03_YoU_F41l}'
</pre>
