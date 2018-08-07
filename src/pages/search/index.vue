<template lang="html">
    <div class="container">
        <div class="search-title">
            <div class="search-input">
                <img src='/static/images/search.png'>
                <input 
                    placeholder="请输入学校名称（不含军校）" 
                    v-model="value"
                    @input="handleInput"
                >
                <img
                    v-if="value"
                    src='/static/images/delete.png'
                    @click="cleanInput"
                />
            </div>
            <button  @click="cleanInput">取消</button>
        </div>
        <div class="hot-list">
            <h2>热门榜单</h2>
            <ul>
                <li v-for="item in items" :key="item.id">
                    {{ item.title }}
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      value: '',
      items: [
        {title: '2018中国985大学排名'},
        {title: '2018中国211大学排名'},
        {title: '2018中国前十的理工大学'},
        {title: '2018中国十大综合类大学排名'},
        {title: '2018中国医术技术专业大学排名'},
        {title: '2018最新军校名单'}
      ]
    }
  },
  methods: {
    handleInput (event) {
      this.value = event.target.value
      this.$emit('input', event.target.value)
    },
    cleanInput () {
      this.$emit('input', '')
      this.value = ''
    }
  }
}
</script>

<style lang="less">
.search-title {
    padding: 15rpx 20rpx;
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid #eeeeee;
    .search-input {
        background-color: #e6e6e6;
        display: inline-flex;
        width: 500rpx;
        padding-left: 5rpx;
        img{
            display: block;
            width:44rpx;
            height:33rpx;
            padding:14rpx 0;
        }
        input{
        display: block;
        width: 400rpx;
        padding:4rpx 0;

        }
    }
    button {
        padding: 0 8rpx;
        font-size: 12px;
        border: 0rpx;
        background-color: #ffffff;
    }
}
.hot-list {
    padding-top: 40rpx;
    h2 {
        border-bottom: 1px solid #eeeeee;
        padding-bottom: 15rpx;
        margin-left: 15rpx;
    }
    h2::before{
        content:'\0020';
        color: red;
    }
    ul li {
        margin-left: 15rpx;
        border-bottom: 1px solid #eeeeee;
        padding:20rpx 15rpx;
    }
    
}
</style>
