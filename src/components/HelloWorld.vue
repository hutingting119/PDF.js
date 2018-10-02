<template>
  <div class="page-one">
    <p>pdf.js demo</p>
    <!--本地-->
    <div style="margin-top: 10px">
      <p>本地</p>
      <button @click="checkLocal">点击一下</button>
    </div>
    <!--服务器-->
  <div style="margin-top: 30px">
    <p>服务器</p>
    <button @click="checkSuccess">查看服务器跨域返回流</button>
  </div>
  </div>
</template>

<script>
export default {
  name: 'page-one',
  data () {
    return {
        fileUrl: '',
        showPdf: false
    }
  },
  methods: {
      checkLocal () {
          let url = 'demo.pdf'
          window.open('/static/pdf/web/viewer.html?file=' + url)
      },
    checkSuccess () {
         // 后台返回流的形式，也是我本人项目的使用
      let url = 'https://dluat.hscf.com/api/esm/v1/contractTemplates/load/c08def54aa40412b8b511406fc0271d2/0?access_token=b6cce0c8428c55531d206b4f008fe44e&name=cehsi.pdf'
      // 当然上面的是可以的，但是此access_token 是有时效性的，只是放在这边当作个例子，至于最后我为什么加了个测试.pdf 是可以在浏览器标签叶上显示
      window.open('/static/pdf/web/viewer.html?file=' + encodeURIComponent(url))
    },
  }
}
</script>

<style scoped>
  .page-one button{
    margin-left: 10px;
  }
</style>
