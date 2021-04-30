<template>
 <form @submit.prevent="handleFormSubmit">
   <h3 class="form-section-title">Информация пользователя</h3>
    <div class="form-group">
      <div class="input-duoble-wrap">
        <div class="input-container">
          <input type="text"  v-model.trim="lastName" :class="{invalid: $v.lastName.$invalid}" required>
          <label>Фамилия<span class="require">*</span></label>
          <span class="line"></span>
        </div>
        <span v-if="$v.lastName.$invalid" class="message">Укажите фамилию</span>
      </div>
      <div class="input-duoble-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="name" :class="{invalid: $v.name.$invalid}" required>
          <label>Имя<span class="require">*</span></label>
          <span class="line"></span>
        </div>
        <span class="message" v-if="$v.name.$invalid">Укажите Имя</span>
      </div>
    </div>

    <div class="form-group">
      <div class="input-duoble-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="patronymic" :class="{invalid: $v.patronymic.$invalid}">
          <label>Отчество</label>
          <span class="line"></span>
        </div>
        <span v-if="$v.patronymic.$invalid" class="message">Отчество введено не корректно</span>
      </div>
    </div>

    <div class="form-group">
      <div class="input-duoble-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="dateOfBirth" required :class="{invalid: $v.dateOfBirth.$invalid}">
          <label>Дата рождения<span class="require">*</span></label>
          <span class="line"></span>
        </div>
        <span v-if="$v.dateOfBirth.$invalid" class="message">Формат - (01.01.1999)</span>
      </div>
      <div class="input-duoble-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="phone" required :class="{invalid: $v.phone.$invalid}">
          <label>Номер телефона<span class="require">*</span></label>
          <span class="line"></span>
        </div>
        <span v-if="$v.phone.$invalid" class="message">Формат - 79999999999</span>
      </div>
    </div>

    <div class="form-group">
      <div class="input-duoble-wrap">
        <div class="radio-control">
          <span>Пол</span>
          <div class="custom-radio">
            <label>
              <input name="radio" type="radio" value="male" required checked v-model="male">
              <span class="radio"></span>
              <span class="label">Мужской</span>
            </label>
          </div>
          <div class="custom-radio">
            <label>
              <input name="radio" type="radio" value="female" required v-model="male">
              <span class="radio"></span>
              <span class="label">Женский</span>
            </label>
          </div>
        </div>
      </div>
    </div>

    <div class="form-group">
      <div class="input-duoble-wrap">
        <div class="input-container">
          <div style="display: flex; align-items: flex-start;">
            <select class="my-select multiple" multiple size="3" v-model="clientsGroup" required>
              <option disabled value="">Группа клиентов</option>
              <option value="VIP">VIP</option>
              <option value="Проблемные">Проблемные</option>
              <option value="ОМС">ОМС</option>
            </select>
            <span class="require">*</span>
          </div>
        </div>
        <span v-if="$v.clientsGroup.$invalid" class="message">Выберите группу клиентов</span>
      </div>
      <div class="input-duoble-wrap">
        <div class="input-container">
          <select class="my-select" v-model="doctor">
            <option disabled selected value="">Лечащий врач</option>
            <option value="Иванов">Иванов</option>
            <option value="Захаров">Захаров</option>
            <option value="Чернышева">Чернышева</option>
          </select>
        </div>
      </div>
    </div>

    <div class="form-group">
      <div class="input-duoble-wrap">
        <div class="checkbox-container">
          <label>
            <input type="checkbox" name="check" v-model="sms">
            <span class="checkbox"></span>
            <span class="label">Не отправлять СМС</span>
          </label>
        </div>
      </div>
    </div>

    <h3 class="form-section-title">Адресс</h3>

    <div class="form-group">
      <div class="input-tripple-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="townIndex">
          <label>Индекс</label>
          <span class="line"></span>
        </div>
      </div>
      <div class="input-tripple-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="country">
          <label>Страна</label>
          <span class="line"></span>
        </div>
      </div>
      <div class="input-tripple-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="region">
          <label>Область</label>
          <span class="line"></span>
        </div>
      </div>
    </div>

    <div class="form-group">
      <div class="input-tripple-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="town" required :class="{invalid: $v.town.$invalid}">
          <label>Город<span class="require">*</span></label>
          <span class="line"></span>
        </div>
        <span v-if="$v.town.$invalid" class="message">Укажите город</span>
      </div>
      <div class="input-tripple-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="street">
          <label>Улица</label>
          <span class="line"></span>
        </div>
      </div>
      <div class="input-tripple-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="house">
          <label>Дом</label>
          <span class="line"></span>
        </div>
      </div>
    </div>

    <h3 class="form-section-title">Документ</h3>

    <div class="form-group">
      <div class="input-tripple-wrap">
        <div class="input-container">
          <div style="display: flex; align-items: flex-start;">
            <select class="my-select" v-model="documentType" required>
              <option disabled selected value="" >Тип документа</option>
              <option value="Паспорт">Паспорт</option>
              <option value="Свидетельство о рождении">Свидетельство о рождении</option>
              <option value="Вод. удостоверение">Вод. удостоверение</option>
            </select>
            <span class="require">*</span>
          </div>
        </div>
        <span v-if="$v.documentType.$invalid" class="message">Выберите тип документа</span>
      </div>
      <div class="input-tripple-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="documentSeries">
          <label>Серия</label>
          <span class="line"></span>
        </div>
      </div>
      <div class="input-tripple-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="documentNumber">
          <label>Номер</label>
          <span class="line"></span>
        </div>
      </div>
    </div>

    <div class="form-group">
      <div class="input-duoble-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="documentIssued">
          <label>Кем выдан</label>
          <span class="line"></span>
        </div>
      </div>
      <div class="input-duoble-wrap">
        <div class="input-container">
          <input type="text" v-model.trim="documentDateOfIssue" required :class="{invalid: $v.town.$invalid}">
          <label>Дата выдачи<span class="require">*</span></label>
          <span class="line"></span>
        </div>
        <span v-if="$v.documentDateOfIssue.$invalid" class="message">Формат - (01.01.1999)</span>
      </div>
    </div>

    <div class="info">
      <span class="require">*</span><span>- Обязательные поля</span>
    </div>

    <div class="btn-container">
      <button class="create-btn" type="submit">Создать</button>
    </div>

  </form>
</template>


<script>
import { required, minLength } from 'vuelidate/lib/validators';

export default {
  name: 'clientForm',

  data(){
    return {
      name: '',
      lastName: '',
      patronymic: '',
      dateOfBirth: '',
      phone: '',
      male: 'male',
      clientsGroup: [],
      doctor: '',
      sms: false,
      townIndex: '',
      country: '',
      region: '',
      town: '',
      street: '',
      house: '',
      documentType: '',
      documentSeries: '',
      documentNumber: '',
      documentIssued: '',
      documentDateOfIssue: ''
    }
  },

  validations: {
    lastName: {
      required,
      minLength: minLength(2)
    },
    name: {
      required,
      minLength: minLength(2)
    },
    patronymic: {
      minLength: minLength(2)
    },
    dateOfBirth: {
      required,
      minLength: minLength(5),
      isRightFormat(value) {
        return new RegExp(/^(\d{2}\.){2}\d{4}$/).test(value)
      }
    },
    phone: {
      required,
      isRightFormat(value) {
        return new RegExp(/^7\d{10}$/).test(value)
      }
    },
    clientsGroup: {
      notEmpty(value) {
        return value.length > 0;
      }
    },
    town: {
      required,
      minLength: minLength(2)
    },
    documentType: {
      required
    },
    documentDateOfIssue: {
      required,
      isRightFormat(value) {
        return new RegExp(/^(\d{2}\.){2}\d{4}$/).test(value)
      }
    }
  },

  methods: {
    handleFormSubmit(event){
      const formData = {
        name: this.name,
        lastName: this.lastName,
        dateOfBirth: this.dateOfBirth,
        phone: this.phone,
        clientsGroup: this.clientsGroup,
        town: this.town,
        documentType: this.documentType
      };

      if (this.$v.$invalid) {
        window.alert('Форма заполнена не правильно');
        return ;
      }

      this.$emit('openModal', formData);
      event.target.reset();

      this.name = '',
      this.lastName = '',
      this.patronymic = '',
      this.dateOfBirth = '',
      this.phone = '',
      this.male = 'male',
      this.clientsGroup = [],
      this.doctor = '',
      this.sms = false,
      this.townIndex = '',
      this.country = '',
      this.region = '',
      this.town = '',
      this.street = '',
      this.house = '',
      this.documentType = '',
      this.documentSeries = '',
      this.documentNumber = '',
      this.documentIssued = '',
      this.documentDateOfIssue = ''
    }
  }
}
</script>