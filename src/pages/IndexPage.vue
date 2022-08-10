<template>
  <div v-for="news in newsDatas" :key="news.url">{{ news.title }}</div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import axios from "axios";

const newsDatas = ref([]);

onMounted(() => {
  axios
    .get(
      "https://newsapi.org/v2/everything?q=tesla&from=2022-07-10&sortBy=publishedAt&apiKey=283ee2e3a7104bd681733595977634a3"
    )
    .then((res) => {
      /*
        author: "Sputnik Việt Nam"
        content: "Musk có th tip tc bán c phiu Tesla, hoc có th dng li. Cng rt khó nói Elon Musk mu gì. Rõ ràng là ông y cn s tin này gii quyt mt s vn khá thc t, ông y là mt ngi rt thc t, con ngi ca công vic. Có th, ô… [+329 chars]"
        description: "MATXCƠVA (Sputnik) - Elon Musk đã bán số cổ phiếu Tesla trị giá gần 7 tỷ USD, theo các phương tiện truyền thông. Trong một cuộc phỏng vấn với Sputnik, nhà báo phụ trách chuyên mục của IT Channel News Alexander Malyarevsky đã bình luận về tình huống này."
        publishedAt: "2022-08-10T08:33:53Z"
        source: {id: null, name: 'Sputnik International'}
        title: "Elon Musk đang ủ mưu gì? Chuyên gia bình luận về việc tỷ phú bán cổ phiếu Tesla"
        url: "https://vn.sputniknews.com/20220810/elon-musk-dang-u-muu-gi-chuyen-gia-binh-luan-ve-viec-ty-phu-ban-co-phieu-tesla-16965734.html"
        urlToImage: "https
      */
      newsDatas.value = res.data.articles;
    });
});
</script>
