DataLazyload
============

�����ӳټ������.
�ܶ�ʱ��, �û��ڵ�һ���ͷ�������ת, ������δ��¶�桱��ͼƬ���ض��û���˵���������.
`DataLazyload` ���� �����⡱ �û�����Ϊ, ���û��뿴ĳ������ʱ, �ſ�ʼ������������ͼƬ.
�����ӳ�ͼƬ����, DataLazyload �������ӳ�ĳ����������� html ����Ⱦ, ��� Tabs �� UI �����������, ���������ҳ�������.

## ���ʹ��
```js
KISSY.use('datalazyload',function(S,DataLazyload){
    // use DataLazyload
});
```
### [demo](../demo/index.html)

## Class
* DataLazyload

## Configs
* diff
* placeholder
* execScript
* autoDestroy
* onStart

## Methods
* addCallback()
* removeCallback()
* addElements()
* removeElements()
* getElements()
* refresh()
* pause()
* resume()
* destroy()

## Static Methods
* loadCustomLazyData()
* isWebpSupported()

## Class Detail
### DataLazyload (config)
* �̳��� Base
* Parameters:
 * config (Object) �C ������, ��ϸ���·� `Configs Detail`.

*Note*
��������Ҫ�����ص�ͼƬ����ʵ��ַ��Ҫ���� `data-ks-lazyload ��`�� ��Ҫ�����ص� `textarea` ��߱���ʽ�� `ks-datalazyload`

## Configs Detail
* autoDestroy
  * {Boolean} - Ĭ��Ϊ true , ����ʼ��ʱ��⵽��������������Ԫ�ض�������Ϻ��Ƿ��Զ����� destroy ����
* container
  * {String|HTMLElement} - Ĭ��Ϊ document , ͼƬ������������������Ԫ���������к��Ӵ���ͬʱ����ʱ������Ⱦ��
* diff
  * {Number|Object} -
  * Number ����ʱ��ǰ�Ӵ�����, diff px ��� img/textarea �ӳټ���, �ʵ����ô�ֵ, �������û����϶�ʱ�о������Ѿ����غ�, Ĭ��Ϊ��ǰ�Ӵ��������Ӵ����߶�(��������Ĳ��ӳټ���).
  * Object ���Ϳ���ָ�� left/top/right/bottom ��ֵ����ʾԤ���ص�ǰ�Ӵ��������Ӵ��������������ҵľ����Ԫ��.
* placeholder
  * {String} - Ĭ��Ϊ http://a.tbcdn.cn/kissy/1.0.0/build/imglazyload/spaceball.gif, ���������ͼ��û������ src ����Ϊͼ���ռλͼ.
* execScript
  * {Boolean} - Ĭ��Ϊ true , �Ƿ�ִ�� textarea ����Ľű�.
* onStart
  * {Function} Ĭ��ֵΪ null, �滻 src ֮ǰ���õĺ���, ���Զ�ͼƬ��ַ������, �� webp �ļ���
    * {Function}, �Ƽ�
      ```js
      DataLazyload.isWebpSupported(function(isSupported) {
          var conf = {};
          if (isSupported) {
              /**
               * obj {Object}
               *  - type: 'img' || 'textarea'
               *  - elem: HtmlElement
               *  - src ��� type �� 'img', �����������, ΪͼƬ��ַ
               *  - value ��� type �� 'textarea', �����������, Ϊ textarea.value
               */
              conf.onStart = function(obj) {
                if (obj.type == 'img') {
                  var src = obj.data.src;
                  if (src.indexOf('taobaocdn.com') !== -1 && (src.indexOf('.jpg') || src.indexOf('.png'))) {
                    src += '_.webp';
                  }

                  S.log(src);

                  return src;
                }
              };
          }
          DataLazyload('#J_webpEnabled', conf);
      });
      ```

## Methods Detail
* addCallback (el, fn)
  * ��ӻص�����. �� el ������������ͼ��ʱ, ���� fn
* removeCallback (el, fn)
  * ɾ���ص�����. ����ͬ addCallback
* addElements (els)
  * ���Ԫ�ص��������б�.
  * Parameters:
     * els (HTMLElement[]) �C �µ�������Ԫ���б�
* removeElements (els)
  * ���������б���ɾ��Ԫ��.
  * Parameters:
     *  els (HTMLElement[]) �C ���е�������Ԫ���б�
* getElements ()
  * �õ�������Ԫ���б�
  * ::returns: {Object} eg: {images:[],textareas:[]}
* refresh ()
  * ǿ�����̼��������Ԫ��
* pause ()
  * ��ͣ���������Ԫ��
* resume ()
  * �������������Ԫ��
* destroy ()
  * ֹͣ��ز��������

## Static Methods Detail
* static loadCustomLazyData (containers, type)
  * �����Զ����ӳ�����
  * Parameters:
     * containers (HTMLElement[]) �C �����Զ����ӳټ����������Ԫ��
     * type (String) �C �ӳټ��ط�ʽ, ��ȡ:
         - `textarea` �� `area-data` , ����ʾ�ӳټ���ʹ�õ��� textarea ��ʽ;
             ��ʱ textarea ��Ҫ����ʽ�� `ks-datalazyload-custom`
         - `img` �� `img-src`, ����ʾ�ӳټ���ʹ�õ��� img ��ʽ.
            ��ʱ img ����ʵ��ַ��������� `data-ks-lazyload-custom` ��

* static isWebpSupported (callback)
  * ������Ƿ�֧�� webp
  * Parameters:
    * callback (Function) - ����һ������{Boolean}, ��ʾ������Ƿ�֧�� webp ��ʽ

## Note
�� ��һ�����ò���Ϊ����ʱ�������ģʽ( 1.2 )����ʱ������Ԫ���Ƿ���Ⱦ���ж��Ƿ��������ڣ�ֻ�ж��Ƿ�������Ӵ��С�����
```js
new DataLazyLoad([document.getElementById('x1'),document.getElementById('x2')]);
```
*��������ע�⣺*
- autoDestroy ����Ĭ��Ϊ true ����ô����ʼ��ʱ��⵽��������������Ԫ�ض�������Ϻ���Զ����� destroy ��������������������ж�̬��ӵ�������Ԫ�أ������� autoDestroy ����Ϊfalse�����ں����ֶ����� destroy ����

- ��ע��ʵ���������������Ƕ�׵� datalazyload ʱ�ظ�������⣬����

    ʵ��1
    
    ```js
    new DataLazyLoad({
        container: document
    });
    ```
    
    ʵ��2
    
    ```js
    new DataLazyLoad({
        container: '#xx'
    });
    ```
    
    �� `#xx` ��������Ԫ����ʵ��1ʵ����ǰ�ʹ��ڣ���ᵼ��ʵ��1��ʵ��2�ظ����ͬһԪ������.



- ��ע�ⲻ��ʾԪ�صļ�⣬����ʵ��
    
    ```js
    var  = new DataLazyLoad({
        container: '#yy'
    });
    ```
    ��ĳ������£����� tab �л����� `#yy.display='none'`��֮������м�ض��������˷�. ��ʱ���Ե��� `pause` ��������ͣ��ʵ���ļ�⣬
    
    ```js
    d.pause();
    ```
    ���ٴ� tab �л���`#yy.display=''` ������ resume �����¼��.
    
    ```js
    d.resume();
    ```
