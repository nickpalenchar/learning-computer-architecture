 
1.

```
a = 2
b = a
```

```asm
addi $s2,$s2,2
add $s3,$zero,$s2
```

2)

```
a += 3
c = a * 2
b = a + c
```

```asm
addi $s1,$s1,3
add $s3,$s1,$s1
add $s2,$s1,$s3
```

3)
```asm
a = (a + b) - (c + d)

add $t1,$s1,$s2
add $t2,$s3,$s4
andi $s1,$zero,0
# TODO set $s2 to negative
add $s1,$t1,$t2
```

4)

```
while (a != b)
  a += 1
```

```asm
Loop:beq $s0,$s1,Exit
addi $s0,$s0,1
j Loop
Exit:
```

5

```
while (i < a.length)
  b += a[i]
  i += 1
```

```
$s0 <- base of a
$t1 <- a.length
$s2 <- b
$s3 <- i
```

```asm
Loop:slt $t0,$s3,$t1
beq $t0,$zero,End
sll $t2,$t1,2
lw $t3,$t2($s0)
add $b2,$b2,$t3
addi $s3,1
j Loop
End:
```
