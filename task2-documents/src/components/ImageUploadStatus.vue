<template>
  <div class="image-status">
    <UploadImg v-if="imgType == 'upload' || imgType == 'reject'"/>
    <WaitImg v-if="imgType == 'wait'"/>
    <OkImg v-if="imgType == 'ok'"/>
    <LoadingImg v-if="imgType == 'loading'"/>
  </div>
</template>

<script>
import UploadImg from '@/assets/img/upload.svg';
import WaitImg from '@/assets/img/wait.svg';
import OkImg from '@/assets/img/ok.svg';
import LoadingImg from '@/components/LoadingImg';

export default {
  name: 'ImageUploadStatus',
  components: {
    UploadImg,
    WaitImg,
    OkImg,
    LoadingImg
  },
  props: {
    imgType: String
  },
  created: () => {
    console.log(this);
  }
}
</script>

<style lang="scss">
.image-status {
  padding: 8px;
  border-radius: 8px;
  background-color: #fff;
}
</style>
