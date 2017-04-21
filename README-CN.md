## ��ѶAlloyTeam��ʽ����Webħ������ - curvejs

[curvejs](https://github.com/AlloyTeam/curvejs) ���Ķ�["��js"]������ѶAlloyTeam�����һ��ħ��������ܣ���������Ϊһ����������ߣ��������ǳ�Ϊ��������ţ�HTML5 Canvas������̨��

������[https://alloyteam.github.io/curvejs/](https://alloyteam.github.io/curvejs/)

�㻹�ǵ�window�������Ļ�������򡶱���ߡ���

![](http://images2015.cnblogs.com/blog/105416/201704/105416-20170421100349227-820259243.png)

��ԭ�����ʹ�� Perlin-Noise + Particle System + B��zier curve + Color Transition �������ɡ�

ʹ��curvejsʵ�����Ʊ���߹���ֻ��Ҫ����10�д��룺

```js
const  { Stage, Curve, motion } = curvejs

let stage = new Stage(document.getElementById('myCanvas'))

stage.add(new Curve({
    color: '#00FF00',
    data: {value: 0, step: 0.008, width: 600, height: 400},
    motion: motion.noise
}))
```

?[�����ַ](https://alloyteam.github.io/curvejs/pg/rd.html?type=noise)

��Ȼ��curvejs�������������Ǳ任�ߣ�����ȫȡ������������������磺

* [Points-To](https://alloyteam.github.io/curvejs/pg/rd.html?type=points-to)
* [Rotate](https://alloyteam.github.io/curvejs/pg/rd.html?type=rotate)
* [Word](https://alloyteam.github.io/curvejs/pg/rd.html?type=word)
* [Perlin-Noise](https://alloyteam.github.io/curvejs/pg/rd.html?type=noise)
* [Simple](https://alloyteam.github.io/curvejs/pg/rd.html?type=simple)
* [Simple-ES5](https://alloyteam.github.io/curvejs/pg/rd.html?type=simple-es5)
* [Curves](https://alloyteam.github.io/curvejs/pg/rd.html?type=curves)
* [Line](https://alloyteam.github.io/curvejs/pg/rd.html?type=line)
* [Close](https://alloyteam.github.io/curvejs/pg/rd.html?type=close)

## ʹ��ָ��

```bash
$ npm install curvejs
```

```javascript
import curvejs from 'curvejs'
```

Ҳ����ֱ�Ӳ���script�����HTMLҳ��:

```html
<script src="https://unpkg.com/curvejs@0.2.0/dist/curve.min.js"></script>
```

��ʼ����:

```js
var Stage = curvejs.Stage,
    Curve = curvejs.Curve,
    canvas = document.getElementById('myCanvas'),
    stage = new Stage(canvas),
    rd = function() {
     return -2 + Math.random() * 2
    }

var curve = new Curve({
  color: '#00FF00',
  points: [277, 327, 230, 314, 236, 326, 257, 326],
  data: [rd(), rd(), rd(), rd(), rd(), rd(), rd(), rd()],
  motion: function motion(points, data) {
      points.forEach(function (item, index) {
          points[index] += data[index]
      })
  }
})

stage.add(curve)

function tick(){
  stage.update()
  requestAnimationFrame(tick)
}

tick()
```

�����points���������α��������ߵ�4���㡣motion�����˶���ʽ��motion������ȥ��points��data��motion�ﺯ����thisָ��Curve��ʵ��curve��


## ʹ������motion

```js
var curve = new Curve({
  points: [277, 327, 230, 314, 236, 326, 257, 326],
  data: {angle: 0, r:5 ,step:Math.PI / 50 }
  motion: curvejs.motion.dance
})
```

## �ύ���motion

�� [ motion Ŀ¼](https://github.com/AlloyTeam/curvejs/tree/master/src/motion), ��������õ�motion�ṩ��������ʹ�ã�������Ҳ�����ύ���motion�������Ŀ���һ��һʱ��review���������ɡ�

����motion��ʽ����:

```js
/**
 * motion description.
 *
 * @param {points}
 * @param {data}
 *      data rule example:
 *      [1, 0.2, -3, 0.7, 0.5, 0.3, -1, 1]
 */
export default function (points, data) {
    //���motion�߼�
}
```

## ����ԭ��
![](http://images2015.cnblogs.com/blog/105416/201704/105416-20170421100408884-843332110.png)


* ÿ�δ���Curve ���Դ���˸����֣���ʵ�ʹ��������4���������
* motion������õ� points �����Զ�����
* ��Ӱ����Ҫ�����߿��ǣ�curvejs���Զ����ɻ�Ӱ

������Ҫ�ر�ǿ����curvejs�Ļ�Ӱ��������canvas�ĺ�ɫ�ף�Ȼ��fillRect����͸������������Particle System������curvejs��������Ч������һ���Ǻ�ɫ����������canvasҲ������͸������ʹ�����������ó�����

## Omi���

* ������[https://alloyteam.github.io/curvejs/](https://alloyteam.github.io/curvejs/)
* Github: [https://github.com/AlloyTeam/curvejs](https://github.com/AlloyTeam/curvejs)
* ���ӷ���Ľ�������curvejs��һ�п��Լ���QQ��curvejs����Ⱥ(179181560)