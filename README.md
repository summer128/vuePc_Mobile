# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

遇见的问题集合
1.PC端网址不能带有#符号
  //如果就只设置mode: 'history',PC端出现首页不显示问题
  解决：router/pc/index.js中设置 mode: 'history'，base:'/p_index.html',一定要设置base指定p_index.html或者m_index.html
  
2.移动端px2rem不能使用，因为要修改公共的build文件夹下的utils.js文件（具体操作自行百度），一旦加入此插件PC端也将会执行px-rem,造成PC页面混乱

  解决：在framework/mobile/m_index.html中添加以下代码
        (function () {
              function resize() {
                  var baseFontSize = 100; //设计稿100px相当于1rem
                  var designWidth = 750;//设计稿宽度
                  var width = window.innerWidth;//获取屏幕宽度
                  var currentFontSize = (width / designWidth) * baseFontSize;//
                  document.querySelector('html').style.fontSize = currentFontSize+'px';//html的真实数值
              }
              window.onresize = function () {
                 resize()
              }
              document.addEventListener('DOMContentLoaded',resize)
         }())
         
         **写具体样式自行转rem**
         
 
