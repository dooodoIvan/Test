<template>
  <div class="wrapper">
    <div class="test">
      <div class="test__header">
        <h1>Регистрация</h1>
      </div>
      <div class="test__form">
        <div class="test__form__block">
          <div>
            <div>
              <h2>Атрибуты формы</h2>
            </div>
            <div class="test__form__block__input">
              <input v-model.lazy="surname" type="text" />
              <label>Фамилия</label>
              <p v-if="!$v.surname.required">Заполните</p>
            </div>
            <div class="test__form__block__input">
              <input v-model.lazy="name" type="text" />
              <label>Имя</label>
              <p v-if="!$v.name.required">Заполните</p>
            </div>
            <div class="test__form__block__input">
              <input v-model="patronymic" type="text" required />
              <label>Отчество</label>
            </div>
          </div>
          <div>
            <div class="test__form__block__input">
              <input v-model="dateBirth" type="text" required />
              <label>Дата рождения</label>
            </div>
            <div class="test__form__block__input">
              <input type="text" required />
              <label>Номер телефона</label>
            </div>
            <div class="test__form__block__input">
              <input v-model="gender" type="text" required />
              <label>Пол</label>
            </div>
          </div>
          <div>
            <div>
              <h3>Группа клиентов</h3>
              <select v-model="clientsGroup" multiple>
                <option>VIP</option>
                <option>Проблемные</option>
                <option>ОМС</option>
              </select>
            </div>
            <div>
              <h3>Лечащий врач</h3>
              <select v-model="doctor">
                <option>Иванов</option>
                <option>Захаров</option>
                <option>Чернышева</option>
              </select>
            </div>
            <div>
              <h3>Не отправлять СМС</h3>
              <input v-model="sms" type="checkbox" />
            </div>
          </div>
        </div>
        <div class="test__form__block">
          <div>
            <h2>Адрес</h2>
          </div>
          <div class="test__form__block__input">
            <input v-model="index" type="text" required />
            <label>Индекс</label>
          </div>
          <div class="test__form__block__input">
            <input v-model="country" type="text" required />
            <label>Страна</label>
          </div>
          <div class="test__form__block__input">
            <input v-model="region" type="text" required />
            <label>Область</label>
          </div>
          <div class="test__form__block__input">
            <input v-model="city" type="text" required />
            <label>Город</label>
          </div>
          <div class="test__form__block__input">
            <input v-model="street" type="text" required />
            <label>Улицы</label>
          </div>
          <div class="test__form__block__input">
            <input v-model="home" type="text" required />
            <label>Дом</label>
          </div>
        </div>
        <div class="test__form__block">
          <div>
            <div>
              <h2>Паспорт</h2>
            </div>
            <h3>Тип документа</h3>
            <select v-model="document">
              <option>Паспорт</option>
              <option>Свидетельство о рождении</option>
              <option>Вод. удостоверение</option>
            </select>
          </div>
          <div class="test__form__block__input">
            <input v-model="seriesDocument" type="text" required />
            <label>Серия</label>
          </div>
          <div class="test__form__block__input">
            <input v-model="numberDocument" type="text" required />
            <label>Номер</label>
          </div>
          <div class="test__form__block__input">
            <input v-model="whoIssued" type="text" required />
            <label>Кем выдан</label>
          </div>
          <div class="test__form__block__input">
            <input v-model="dateIssue" type="text" required />
            <label>Дата выдачи</label>
          </div>
        </div>
      </div>
      <div class="test__button">
        <button @click="click" type="submit" :disabled="$v.$invalid">Зарегистрроваться</button>
      </div>
    </div>
  </div>
</template>

<script>
import { required } from "vuelidate/lib/validators";

export default {
  name: "app",
  data() {
    return {
      surname: "",
      name: "",
      patronymic: "",
      dateBirth: "",
      phoneNumber: "",
      gender: "",
      clientsGroup: [],
      doctor: "",
      sms: "",
      index: "",
      country: "",
      region: "",
      city: "",
      street: "",
      home: "",
      document: "",
      seriesDocument: "",
      numberDocument: "",
      whoIssued: "",
      dateIssue: "",
    };
  },
  validations: {
    surname: {
      required,
    },
    name: {
      required,
    },
  },
  components: {
    appGame: Game,
  },

  methods: {
    click() {
      alert("dcrrr ");
    },
  },
};
</script>

<style lang="scss">
body {
  margin: 0px;
}

.wrapper {
  margin: 0px;
  display: block;
  background-color: cadetblue;
}

h1 {
  color: white;
  margin-top: 40px;
}

h2 {
  margin-bottom: 20px;
}

.test {
  background-color: #262427;
  font-family: fantasyVerdana, Arial, Helvetica, sans-serif;
  color: #eae7f9;
  border: cadetblue solid 15px;
  border-radius: 30px;

  &__header {
    display: flex;
    justify-content: center;
  }

  &__form {
    display: flex;
    align-items: space-around;
    justify-content: space-around;

    @media (max-width: 1024px) {
      display: inline;

      &__block {
        @media (max-width: 1024px) {
          width: 70%;
          margin-left: 50px;
        }
      }
    }

    &__block__input {
      position: relative;
      margin-bottom: 45px;
      font-size: 30px;
    }

    label {
      margin-left: 20px;
    }

    input {
      font-size: 30px;
      padding: 10px 10px 10px 5px;
      display: block;
      width: 300px;
      border: none;
      border-radius: 25px;
      background-color: cadetblue;
      margin-top: 30px;
      color: white;

      @media (max-width: 1024px) {
        height: 70px;
        width: 100%;
        font-size: 30px;
      }
    }

    p {
      font-size: 20px;
      margin-top: 1px;
      color: red;
    }

    input:focus {
      outline: none;
    }

    input:focus ~ label,
    input:valid ~ label {
      top: -20px;
      font-size: 20px;
      color: #329afb;
    }

    label {
      color: rgb(216, 216, 216);
      font-size: 18px;
      font-weight: normal;
      position: absolute;
      pointer-events: none;
      left: 5px;
      top: 10px;
      transition: 0.2s ease all;
      -moz-transition: 0.2s ease all;
      -webkit-transition: 0.2s ease all;
    }

    select {
      display: flex;
      justify-content: space-between;
      align-items: stretch;
      height: 50px;
      width: 300px;
      background-color: cadetblue;
      border: none;
      border-radius: 10px;
      color: rgb(216, 216, 216);
      font-size: 18px;
      font-weight: normal;
    }

    option {
      margin: 5px;
    }
  }

  &__button {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 30 0 30 0px;

    button {
      width: 300px;
      height: 50px;
      border: none;
      border-radius: 25px;
      background-color: cadetblue;
      color: white;
      margin-bottom: 50px;
    }
  }
}
</style>
