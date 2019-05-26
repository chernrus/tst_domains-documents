<template>
  <div class="upload__document ">
    <div class="upload__document-image">
      <ImageUploadStatus v-bind:imgType="status"/>
    </div>
    <div class="upload__document-file">
      <input type="file" name="name" id="name">
      <label for="name">{{text}}</label>
      <p>Размер файла не более 5Мб</p>
    </div>
    <div :class="'upload__document-status ' + status">
      {{ statusText[status] }}
    </div>
  </div>
</template>

<script>
import ImageUploadStatus from '@/components/ImageUploadStatus';

export default {
  name: 'AccVerification',
  components: {
    ImageUploadStatus
  },
  data() {
    return {
      status: 'wait',
      statusText: {
        upload: ' ',
        wait: 'Идет проверка',
        ok: 'Проверено',
        reject: 'Отклонено'
      }
    }
  },
  props: {
    name: String,
    text: String
  }
}
</script>

<style lang="scss">
  $red: #d23c31;
  $green: #008605;
  $grey: #9e9e9e;

  .upload__document {
    display: table-row;
    // display: flex;
    // flex-flow: row nowrap;
    // justify-content: space-between;

    div {
      display: table-cell;
    }

    &-image {

    }

    &-file {
      input[type="file"] {
        z-index: -1;
        opacity: 0;
        width: 0;
        height: 0;
        overflow: hidden;
        position: absolute;
      }

      label {
        cursor: pointer;
        text-decoration: underline;
      }
    }

    &-status {

      &.ok {
        color: $green;
      }

      &.reject {
        color: $red;
      }

      &.wait {
        color: $grey;
      }
    }
  }
</style>
