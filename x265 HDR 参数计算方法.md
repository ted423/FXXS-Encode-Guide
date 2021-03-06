# x265 HDR 参数计算方法

HDR 压制参数为 `--master-display "G(13250,34500)B(7500,3000)R(34000,16000)WP(15635,16450)L(10000000,1)" --max-cll=1000,400`

首先，不同的色彩空间有不同的G B R WP 数据

通常，不同的片会有不同的L 数据 以及 max-cll


Mediainfo范例

BT.2020  Olympus Has Fallen 2013
```
Color range : Limited
Color primaries : BT.2020
Transfer characteristics : PQ
Matrix coefficients : BT.2020 non-constant
Mastering display color primaries : BT.2020
Mastering display luminance : min: 0.0001 cd/m2, max: 1000 cd/m2
Maximum Content Light Level : 891 cd/m2
Maximum Frame-Average Light Level : 428 cd/m2
Original source medium : Blu-ray
```

Display P3 会比较多
```
Color range                 : Limited
Color primaries             : BT.2020
Transfer characteristics    : PQ
Matrix coefficients         : BT.2020 non-constant
Mastering display color pri : Display P3
Mastering display luminance : min: 0.0001 cd/m2, max: 1000 cd/m2
Maximum Content Light Level : 479 cd/m2
Maximum Frame-Average Light : 464 cd/m2
```


G B R WP 数据看Mediainfo里的Mastering display color pri


```
Display P3
--master-display "G(13250,34500)B(7500,3000)R(34000,16000)WP(15635,16450)"
BT.2020
--master-display "G(8500,39850)B(6550,2300)R(35400,14600)WP(15635,16450)"
```


Venom 2018 movie mediainfo :
<pre><code>Mastering display luminance : min: <b>0.0050</b> cd/m2, max: <b>4000</b> cd/m2
Maximum Content Light Level : <b>3903</b> cd/m2
Maximum Frame-Average Light Level : <b>1076</b> cd/m2
</code></pre>
In this case master-display=G(13250,34500)B(7500,3000)R(34000,16000)WP(15635,16450)**L(40000000,50)** and max-cll=**3903,1076**

About Maximum Content Light Level and Maximum Frame-Average Light Level ... If those not present -> max-cll=0,0