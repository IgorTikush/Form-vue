<template>
  <form @submit.prevent="submitForm" >
    <div class="form-control" :class="{invalid: v$.surname.$error}">
      <label for="surname">Фамилия</label>
      <input id="surname" name="surname" type="text" v-model="state.surname" />
      <span v-if="v$.surname.$error">Пожалуйста, введите фамилию</span>
    </div>
    <div class="form-control" :class="{invalid: v$.name.$error}">
      <label for="name">Имя</label>
      <input id="name" name="name" type="text" v-model="state.name" /> 
      <span v-if="v$.name.$error">Пожалуйста, введите имя</span>
    </div>
    <div class="form-control">
      <label for="dadname">Отчество</label>
      <input id="dadname" name="dadname" type="text" v-model="state.dadname"/>
    </div>
    <div class="form-control" :class="{invalid: v$.birthday.$error}">
      <label for="birthday">Дата рождения</label>
      <input id="birthday" name="birthday" type="date" v-model="state.birthday"/> <span v-if="v$.birthday.$error">Пожалуйста, введите дату рождения</span>
    </div>
    <div class="form-control">
      <label for="phone">Номер телефона</label>
      <input id="phone" name="phone" type="tel" v-model="state.phoneNumber"/> <span v-if="v$.phoneNumber.$error">Пожалуйста, введите верный номер телефона, который начинается с цифры 7</span>
    </div>
    <div class="form-control">
      <h2>Пол</h2>
      <div>
        <input id="sex-male" name="sex" type="radio" v-model="state.sex" value="male"/>
        <label for="sex-male">Мужской</label>
      </div>
      <div>
        <input id="sex-female" name="sex" type="radio" v-model="state.sex" value="female"/>
        <label for="sex-female">Женский</label>
      </div>
    </div>
    
    <div class="form-control" :class="{invalid: v$.clientGroup.$error}">
      <label>Группа клиентов: </label> 
      <div>
        <input id="client-group-vip" name="client-group" type="checkbox" v-model="state.clientGroup" value="vip" />
        <label for="client-group-vip">VIP</label>
        
      </div>
      <div>
        <input id="client-group-problem" name="client-group" type="checkbox" v-model="state.clientGroup" value="problem"  />
        <label for="client-group-problem">проблемные</label>
        
      </div>
      <div>
        <input id="client-group-OMC" name="client-group" type="checkbox" v-model="state.clientGroup" value="OMC" />
        <label for="client-group-OMC">ОМС</label>
        
      </div>
      <span v-if="v$.clientGroup.$error">Пожалуйста, выберете хотя бы одну группу клиентов</span>
    </div>

    <div class="form-control">
      <label for="doctor">Лечащий врач </label>
      <select  id="doctor" name="doctor" v-model="state.doctor">
        <option value="doctorIvanov">Иванов</option>
        <option value="doctorZaharov">Захаров</option>
        <option value="doctorChernishev">Чернышев</option>
      </select>
    </div>

    <div class="form-control">
      <div>
        <input id="No-sms" name="No-sms" type="checkbox" v-model="state.noSms"/>
        <label for="No-sms">Не отправлять СМС</label>
      </div>
    </div>

    <br>
    <h2>Адрес:</h2>
    <br>
    <div class="form-control">
      <label for="index">Индекс</label>
      <input id="index" name="index" type="text"  v-model="state.address.index"/>
    </div>
    <div class="form-control">
      <label for="country">Страна</label>
      <input id="country" name="country" type="text" v-model="state.address.country"/>
    </div>
    <div class="form-control">
      <label for="region">Область</label>
      <input id="region" name="region" type="text" v-model="state.address.region"/>
    </div>
    <div class="form-control" :class="{invalid: v$.address.city.$error}">
      <label for="city">Город</label>
      <input id="city" name="city" type="text" v-model="state.address.city"/>
      <span v-if="v$.clientGroup.$error">Пожалуйста, введите город</span>
    </div>
    <div class="form-control">
      <label for="street">Улица</label>
      <input id="street" name="street" type="text" v-model="state.address.street"/>
    </div>
    <div class="form-control">
      <label for="building">Дом</label>
      <input id="building" name="building" type="text" v-model="state.address.building"/>
    </div>
    <br>
    <!-- почему поле называется паспорт, а документы на выбор? -->
    <h2>Паспорт</h2>

    <div class="form-control" :class="{invalid: v$.document.name.$error}">
      <label for="document">Тип документа </label>
      <select  id="document" name="document" v-model="state.document.name">
        <option value="passport">Паспорт</option>
        <option value="certificate">Свидетельство</option>
        <option value="license">Вод.удостоверение</option>
      </select>
      
    </div>
    <span v-if="v$.clientGroup.$error">Пожалуйста, введите тип документа</span>

    <div class="form-control">
      <label for="seria">Серия</label>
      <input id="seria" name="seria" type="text" v-model="state.document.seria"/>
    </div>

    <div class="form-control">
      <label for="number">Номер</label>
      <input id="number" name="number" type="text" v-model="state.document.number"/>
    </div>

    <div class="form-control">
      <label for="issue">Кем выдан</label>
      <input id="issue" name="issue" type="text" v-model="state.document.issue"/>
    </div>

    <div class="form-control" :class="{invalid: v$.document.issueDate.$error}">
      <label for="issue-date">Дата выдачи</label>
      <input id="issue-date" name="issue-date" type="date" v-model="state.document.issueDate"/>
      <span v-if="v$.clientGroup.$error">Пожалуйста, введите дату выдачи</span>
    </div>


    <div>
      <button type="submit">Save Data</button>
    </div>
  </form>
</template>

<script>
import { required, numeric } from 'vuelidate/lib/validators'
import { useVuelidate } from '@vuelidate/core'
import {reactive, computed} from 'vue'

export default {
  setup() {
    const state = reactive({
      surname: '',
      name: '',
      dadname: '',
      birthday: null,
      phoneNumber: null,
      sex: null,
      clientGroup: [],
      doctor: 'doctorZaharov',
      noSms: false,
      address: {
        index: null,
        country: null,
        region: null,
        city: null,
        street: null,
        building: null
      },
      document: {
        name: 'passport',
        seria: null,
        number: null,
        issue: null,
        issueDate: null
      }
    })
    const rules = computed(() => {
      return {
        surname: { required},
        name: { required},
        birthday: { required },
        phoneNumber: { required, numeric, 
        elevenDigit(value) {
          return value.trim().length === 11;
        }, startsFromSeven(value) {
          return Array.from(String(value), Number)[0] === 7
        }},
        clientGroup: { required },
        address: {
          city: {required}
        },
        document: {
          name: {required},
          issueDate: {required}
        }
      }
    })

    const v$ = useVuelidate(rules, state)

    return {
      state,
      v$,
    }

  },
  
  methods: {
    submitForm() {
      this.v$.$validate()
      console.log(this.v$)
      if (!this.v$.$error) {
        alert('Форма успешно заполнена')
        
      } else {
        alert('Форма заполнена неверно')
       
      }
      
    },
    
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Merriweather:wght@300&display=swap');

form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
  font-family: 'Merriweather', serif;
}

.form-control {
  margin: 0.5rem 0;
}

.form-control.invalid input {
  border-color: red;
}

.form-control.invalid label {
  color: red;
}

span {
  color:red;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  border: none;
  outline: none;
  border-bottom: 1px solid #ddd;
  font-size: 1em;
  padding: 5px 0;
  margin: 10px 0 5px 0;
  width: 100%;
}

select {
  width: auto;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type='checkbox'] + label,
input[type='radio'] + label {
  font-weight: normal;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>