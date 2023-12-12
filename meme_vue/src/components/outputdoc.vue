<template>
  <div>
    <button @click="downloadTxtFile">下载文本文件</button>
  </div>
</template>

<script>
export default {
  methods: {
    downloadTxtFile() {
      const jsonData = { key: 'value' };

      // 将JSON数据转为字符串
      const jsonString = JSON.stringify(jsonData, null, 2);

      // 创建Blob对象
      const blob = new Blob([jsonString], { type: 'text/plain' });

      // 生成下载链接
      const downloadLink = document.createElement('a');
      downloadLink.href = URL.createObjectURL(blob);
      downloadLink.download = 'data.txt';

      // 将下载链接添加到页面并模拟点击
      document.body.appendChild(downloadLink);
      downloadLink.click();

      // 清理生成的元素
      document.body.removeChild(downloadLink);
      URL.revokeObjectURL(downloadLink.href);
    },
  },
};
}
</script>

<style scoped>

</style>


