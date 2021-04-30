<template>
  <div class="overlay">
    <div class="modal">
      <div class="modal-header">
        <h2>Пользователь создан</h2>
      </div>
      <div class="modal-content">
        <div class="info-field">
          <span>Фамилия:</span><span>{{userInfo.lastName}}</span>
        </div>
         <div class="info-field">
          <span>Имя:</span><span>{{userInfo.name}}</span>
        </div>
         <div class="info-field">
          <span>Дата рождения:</span><span>{{userInfo.dateOfBirth}}</span>
        </div>
        <div class="info-field">
          <span>Телефон:</span><span>{{userInfo.phone}}</span>
        </div>
        <div class="info-field">
          <span>Группа:</span><span>{{userInfo.clientsGroup.join(', ')}}</span>
        </div>
        <div class="info-field">
          <span>Город:</span><span>{{userInfo.town}}</span>
        </div>
        <div class="info-field">
          <span>Документ:</span><span>{{userInfo.documentType}}</span>
        </div>
      </div>
      <div class="modal-footer">
        <button class="btn-close">Закрыть</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'userInfo',

  props: {
    userInfo: {
      type: Object,
      required: true
    }
  },

  methods: {
    closeModal(event){
      if (event.target.classList.contains('overlay') || event.target.classList.contains('btn-close')) {
        this.$emit('closeModal');
      }
    }
  },

  mounted(){
    document.body.addEventListener('click', this.closeModal);
  },

  destroyed(){
    document.body.removeEventListener('click', this.closeModal);
  }
}
</script>

<style lang="scss" scoped>
$min-height: 400px;

  .overlay {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, .7);
    z-index: 100;
  }

  .modal {
    background-color: white;
    width: 270px;
    height: 500px;
    border-radius: 5px;
    overflow: hidden;
    display: flex;
    flex-direction: column;

    @media screen and (max-height: $min-height) {
        & {
          height: 300px;
          justify-content: space-between;
        }
      }

    .modal-header {
      background-color: rgb(19, 84, 182);
      height: 50px;
      padding: 10px;
      display: flex;
      justify-content: center;
      position: relative;
      color: rgb(218, 218, 218);
    }

    .modal-content {
      padding: 20px 10px;
      display: flex;
      justify-content: center;
      flex-direction: column;
      align-items: center;
      flex-grow: 1;
      justify-content: flex-start;
      overflow-y: auto;

      .info-field {
        display: flex;
        width: 100%;
        justify-content: space-between;
        padding: 10px 0;
        border-bottom: 1px solid grey;
        user-select: none;
        transition: .2s;

        &:hover {
          background-color: rgb(235, 235, 235);
        }

        & > span:first-child {
          font-weight: bold;
        }
      }
    }

    .modal-footer {
      display: flex;
      justify-content: center;
      border-top: 1px solid grey;
      padding: 5px 0;

      & button {
        padding: 10px 15px;
        border-radius: 5px;
        color: white;
        background-color: rgb(12, 12, 12);
        font-family: inherit;
        transition: .2s;
        letter-spacing: .2px;
        border: none;
        outline: none;
        user-select: none;
        font-size: 16px;

        &:hover {
          background-color: rgb(37, 37, 37);
        }
        &:active {
          transform: translateY(-3px);
        }
      }
    }
  }
</style>