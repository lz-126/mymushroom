<template>
  <div class="comment-info">
    <div class="comment-top">
      <div class="top-title">用户评价</div>
      <div class="top-more">更多 ></div>
    </div>
    <div class="info-user">
      <img :src="usericon" alt />
      <span>{{username}}</span>
    </div>
    <div class="info-detail">
      <p>{{commentInfo.content}}</p>
      <div class="info-other">
        <span>{{commentInfo.created | showDate}}</span>
        <span>{{commentInfo.style}}</span>
      </div>
    </div>
    <div class="info-imgs">
      <img :src="item" alt v-for="(item,index) in commentInfo.images" :key="index" />
    </div>
  </div>
</template>

<script>
import { dateFormat } from "../../../commont/date";
export default {
  name: "DetailCommentInfo",
  data() {
    return {
      usericon: "",
      username: ""
    };
  },
  props: {
    commentInfo: {
      type: Object,
      default() {
        return {};
      }
    }
  },
  watch: {
    commentInfo() {
      this.usericon = this.commentInfo.user.avatar;
      this.username = this.commentInfo.user.uname;
    }
  },
  filters: {
    showDate(value) {
      return dateFormat(new Date(value * 1000), "yyyy-MM-dd");
    }
  }
};
</script>

<style scoped>
.comment-info {
  background-color: #fff;
  padding: 5px 12px;
  color: #333;
  border-bottom: 5px solid #f2f5f8;
}
.comment-top {
  height: 50px;
  line-height: 50px;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}
.top-title {
  float: left;
  font-size: 15px;
}
.top-more {
  float: right;
  margin-right: 10px;
  font-size: 13px;
}
.info-user {
  padding: 10px 0 5px;
}
.info-user img {
  width: 42px;
  height: 42px;
  border-radius: 50%;
}
.info-user span {
  position: relative;
  font-size: 15px;
  top: -15px;
  margin-left: 10px;
}
.info-detail {
  padding: 0 5px 15px;
}
.info-detail p {
  font-size: 14px;
  color: #777;
  line-height: 1.5;
}
.info-detail .info-other {
  font-size: 12px;
  color: #999;
  margin-top: 10px;
}
.info-tother .date {
  margin-right: 8px;
}
.info-imgs {
  margin-top: 10px;
}
.info-imgs img {
  width: 70px;
  height: 70px;
  margin-right: 5px;
}
</style>
