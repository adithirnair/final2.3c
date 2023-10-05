<template>
  <div>
    <p>1. Text Interpolation: {{ msg }}</p><br>
    <p v-html="htmlContent"></p><br>
    <button v-bind:id="buttonId">Click ME!!</button><br><br>
    <p> JavaScript Expression: {{ 5 + 5 }}  </p><br>
    <button @click="increment">Count is: {{ count }}</button><br>
    <p>How many strings does the guitar have ?</p>
    <span>{{ GuitarDone }}</span><br>
    <p v-bind:class="textClass">This text has a class binding.</p><br>
    <p v-bind:style="textStyles">This text has an inline style binding.</p><br>
    <ul>
      <li v-for="(value, key, index) in myObject">
        {{ index }}. {{ key }}: {{ value }}
      </li>
    </ul><br>
    <h2>List Rendering with a Range</h2>
    <ul>
      <li v-for="n in 12" :key="n">primary colours {{ n }}</li>
    </ul><br>
    <h2>List Rendering with v-for and v-if</h2>
    <ul>
      <li v-for="user in users" :key="user.id">
        <span>{{ user.name }}</span>
        <span v-if="user.isVerified"> (Verified)</span>
      </li>
    </ul><br>
    <h2>List Rendering with a Component</h2>
    <ul>
      <product-item
        v-for="product in products"
        :key="product.id"
        :product="product"
      ></product-item>
    </ul>

    <button @click="incrementCountInline">Increment (Inline)</button>
    <button @click="incrementCountMethod">Increment (Method)</button>
    <p>Count: {{ count }}</p><br>
    <h2>Form Input Bindings</h2>
    <label for="text-input">Text Input:</label><!-- 8.a) v-model with <input type="text"> -->
    <input type="text" id="text-input" v-model="textInput" /><br />
    <p>Text Input Value: {{ textInput }}</p>

    
    <label for="checkbox-input">Checkbox:</label><!-- 8.a) v-model with <input type="checkbox"> -->
    <input type="checkbox" id="checkbox-input" v-model="checkboxInput" /><br />
    <p>Checkbox Value: {{ checkboxInput }}</p>

    
    <div>
      <label for="radio-input1">Male:</label> <!-- 8.a) v-model with <input type="radio"> -->
      <input type="radio" id="radio-input1" value="Male" v-model="radioInput" />
    </div>
    <div>
      <label for="radio-input2">Female:</label>
      <input type="radio" id="radio-input2" value="Female" v-model="radioInput" />
    </div>
    <p>Pick your gender: {{ radioInput }}</p>

    
    <label for="select-input">Select your favourite beverage:</label> <!-- 8.a) Select Dropdown -->
    <select id="select-input" v-model="selectedOption">
      <option value="Tea">Tea</option>
      <option value="Cappucino">Cappucino</option>
      <option value="IcedCoffee">Iced Coffee</option>
    </select>
    <p>Selected Option: {{ selectedOption }}</p>

    
    <label for="textarea-input">Text area:</label> <!-- 8.a) Textarea for multiline text input -->
    <textarea id="textarea-input" v-model="textareaInput"></textarea>
    <p>Text area Value: {{ textareaInput }}</p>

    <h2>v-model Modifiers</h2>

   
    <label for="lazy-input">Lazy Modifier:</label> <!-- 8.b) v-model modifier, .lazy Modifier -->
    <input type="text" id="lazy-input" v-model.lazy="lazyInput" /><br />
    <p>Lazy Input Value: {{ lazyInput }}</p>

    <label for="number-input">Number Modifier:</label><!-- 8.b) v-model modifier, .number Modifier -->
    <input type="text" id="number-input" v-model.number="numberInput" /><br />
    <p>Number Input Value (as Number): {{ numberInput }}</p>

    <label for="trim-input">Trim Modifier:</label><!-- 8.b) v-model modifier, .trim Modifier -->
    <input type="text" id="trim-input" v-model.trim="trimInput" /><br />
    <p>Trimmed Input Value: {{ trimInput }}</p><br>
    
  </div>
</template>



<script>
import ProductItem from './ProductItem.vue';
export default {
  components: {
    ProductItem, // Register the ProductItem component
  },

  data() {
    return {
      msg: "Welcome to my vue3 website ",
      htmlContent: '<span style="color: pink;">This is  RAW HTML</span>',
      buttonId: "my-button",
      textClass: 'highlight',
      textStyles: {
        color: 'red',
        fontSize: '23px',
      },
      users: [
        { id: 1, name: 'Adithi', isVerified: true },
        { id: 2, name: 'Anandia', isVerified: false },
       
      ],

      products: [ // Add some sample product data
        { id: 1, name: 'Product 1', price: 10 },
        { id: 2, name: 'Product 2', price: 20 },
        { id: 3, name: 'Product 3', price: 30 },
      ],
      textInput: '',
      checkboxInput: false,
      radioInput: '',
      selectedOption: '',
      textareaInput: '',
      lazyInput: '',
      numberInput: 0,
      trimInput: '',
    };
  },
  setup() {
    const count = ref(0);

    //7.a) An Example of Inline Event Handler
    const incrementCountInline = () => {
      count.value++;
    };

    //7.b) An Example of method Event Handler
    const incrementCountMethod = () => {
      count.value++;
    };

    return {
      count,
      incrementCountInline,
      incrementCountMethod,
    };
  },
};
</script>




<script setup>
import { ref, onMounted, reactive, computed } from 'vue'//3. 
const count = ref(0)
function increment() {
  count.value++
}
onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
const instrument = reactive({
  name: 'GUITAR',
  stringcount: [
    'A minor',
    'A major',
    'B minor',
    'F major'
  ]
})
const GuitarDone = computed(() => { //4. Use of Computed Properties. 
  return instrument.stringcount.length > 3 ? 'more than 3' : 'broken piece'
})
const myObject = reactive({
  position: 'index of initial element in a list',
  next: 'index of second element in a list',
   // 6.a)Implementation of v-for with an Object.
})


</script>
