<template>
  <div class="upload__document">
    <div class="upload__document-image">
      <ImageUploadStatus v-bind:imgType="status"/>
    </div>
    <div class="upload__document-file">
      <input type="file" :name="name" :id="name"
        @change="fileHandle">
      <label v-if="status == 'upload' || status == 'reject'" :for="name" class="fl-enabled">{{text}}</label>
      <label v-else-if="status == 'loading'" for="none">{{text}}</label>
      <label v-else-if="status == 'wait'" for="none">Файл загружен</label>
      <label v-else-if="status == 'ok'" for="none">{{successText}}</label>
      <p v-if="status == 'upload' || status == 'loading' || status == 'reject'">Размер файла не более 5Мб</p>
      <p v-else-if="status == 'wait' || status == 'ok'">{{`${fileName} (${fileSize}Кб)`}}</p>
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
      status: 'upload',
      statusText: {
        upload: ' ',
        wait: 'Идет проверка',
        ok: 'Проверено',
        reject: 'Отклонено',
        fileExcess: 'Превышен размер файла'
      },
      fileName: '',
      fileSize: 0
    }
  },
  props: {
    name: String,
    text: String,
    successText: String
  },
  methods: {
    fileHandle(event) {
      this.status = 'loading';
      
      const file = event.target.files[0],
        { fileName, fileSize, status } = this.validateFile(file);

      setTimeout(()=> {
        this.status = status;
        this.fileSize = fileSize || 0;
        this.fileName = fileName || '';
      }, 1000);

      setTimeout(this.confirmUserData, 3000, file);
    },
    validateFile(file) {
      if(!file) return { status: 'upload' };
      if(file.size > 5242880) {
        return { status: 'fileExcess', fileName: file.name, fileSize: file.size};
      }
      else {
        return { status: 'wait', fileName: file.name, fileSize: file.size};
      }
    },
    confirmUserData(file) {
      const rand = Math.floor(Math.random() * 2);

      if(this.status != 'wait') return;
      switch (rand) {
        case 0:
          this.status = 'reject';
          break;
        case 1:
          this.status = 'ok';
          break;
        default:
          this.status = 'upload';
      }
    }
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
      vertical-align: top;
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

        &.fl-enabled {
          cursor: pointer;
          text-decoration: underline;
        }
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
