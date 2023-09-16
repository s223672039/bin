<template>
  <!-- 1. Template Syntax -->
  <div>
    <!-- a. Text Interpolation -->
    <p>{{ message }}</p>
    
    <!-- b. Raw HTML [v-html] -->
    <div v-html="rawHTML"></div>
    
    <!-- c. Attribute Bindings [v-bind:id] -->
    <input :id="inputId" />
    
    <!-- d. JavaScript expressions inside syntax i.e.{{ }} -->
    <p>{{ uppercaseMessage() }}</p>
  </div>

  <!-- 2. Methods -->
  <button @click="changeMessage">Change Message</button>

  <!-- 3. Reactivity Fundamentals -->
  <p>{{ count }}</p>
  <button @click="incrementCount">Increment Count</button>
   <!-- 4. Computed Properties -->
  <div>
      <!-- Displaying a computed property -->
      <p>Computed Property: {{ computedProperty }}</p>

      <!-- Input field bound to data property -->
      <input type="text" v-model="inputValue" />

      <!-- Button to trigger a method that updates the data property -->
      <button @click="updateInputValue">Update Input</button>
    </div>
       <div>
      <!-- 5. Class and Style Bindings -->

      <!-- a. Binding HTML class [v-bind:class] -->
      <div :class="{ 'active': isActive, 'error': hasError }">Class Binding Example</div>

      <!-- b. Binding Inline Styles [v-bind:style] -->
      <div :style="{ 'color': textColor, 'font-size': fontSize + 'px' }">Style Binding Example</div>
    </div>
    <div>
      <!-- 7. Event Handling: Listening to Events -->
    
      <!-- a. Inline Handlers -->
      <button @click="handleClickInline">Click Me (Inline)</button>

      <!-- b. Method Handlers -->
      <button @click="handleClickMethod">Click Me (Method)</button>
    </div>
     <div>
     <!-- 8. Form Input Bindings --> 
      <!-- a. v-model with <input type="text"> -->
      <input type="text" v-model="textValue" />
      <p>Text Value: {{ textValue }}</p>

      <!-- b. v-model modifiers -->
      <input type="text" v-model.trim="trimmedTextValue" />
      <p>Trimmed Text Value: {{ trimmedTextValue }}</p>

      <!-- a. v-model with <input type="checkbox"> -->
      <input type="checkbox" v-model="checkboxValue" />
      <p>Checkbox Value: {{ checkboxValue }}</p>

      <!-- b. v-model modifiers -->
      <input type="checkbox" v-model="lazyCheckboxValue" />
      <p>Lazy Checkbox Value: {{ lazyCheckboxValue }}</p>

      <!-- a. v-model with <input type="radio"> -->
      <input type="radio" value="option1" v-model="radioValue" />
      <input type="radio" value="option2" v-model="radioValue" />
      <p>Radio Value: {{ radioValue }}</p>

      <!-- a. v-model with <select> -->
      <select v-model="selectedOption">
        <option value="option1">Option 1</option>
        <option value="option2">Option 2</option>
      </select>
      <p>Selected Option: {{ selectedOption }}</p>

      <!-- b. v-model modifiers -->
      <input type="number" v-model.number="numericValue" />
      <p>Numeric Value: {{ numericValue }}</p>

      <!-- b. v-model modifiers -->
      <textarea v-model.trim="trimmedTextareaValue"></textarea>
      <p>Trimmed Textarea Value:</p>
      <pre>{{ trimmedTextareaValue }}</pre>
    </div>
      <div>
      <!-- 9. Watchers -->
      <p>Watched Value: {{ watchedValue }}</p>
      <input v-model="inputValue" />

      <!-- 10. Components -->
      <!-- a. Props -->
      <child-component :message="messageFromParent"></child-component>

      <!-- b. Events [$emit] -->
      <button @click="emitCustomEvent">Emit Custom Event</button>

      <!-- c. Slots -->
    <slot-example>
        <p>This content is passed as a slot to the slot-example component.</p>
      </slot-example>

        <!-- 11. Router -->
      <router-link to="/route">Go to Route</router-link>
      <router-view></router-view>
    </div>
</template>

<script>
import { ref } from 'vue';

export default {
  data() {
    return {
      // 1. Template Syntax
      message: 'SIT120 Task 2.3C',
      rawHTML: '<span style="color: cyan;">Raw HTML</span>',
      inputId: 'my-input',

      // 3. Reactivity Fundamentals
      count: ref(0),

      // 4. Computed Properties
      inputValue: 'Hello, Vue!',

      // 5. Class and Style Bindings
      isActive: true,
      hasError: false,
      textColor: 'blue',
      fontSize: 16,
      // 8. Form Input Bindings
      // a. v-model with <input type="text">
      textValue: '',

      // b. v-model modifiers
      trimmedTextValue: '',

      // a. v-model with <input type="checkbox">
      checkboxValue: false,

      // b. v-model modifiers
      lazyCheckboxValue: false,

      // a. v-model with <input type="radio">
      radioValue: '',

      // a. v-model with <select>
      selectedOption: 'option1',

      // b. v-model modifiers
      numericValue: 0,

      // b. v-model modifiers
      trimmedTextareaValue: '',
      // 9. Watchers
      watchedValue: '',
      inputValue: '',

      // 10. Components
     parentMessage: 'Hello from Parent!',
    };
  },
   
   watch: {
    // 9. Watchers
    inputValue(newVal) {
      this.watchedValue = newVal;
    },
  },
  methods: {
    // 2. Methods
    uppercaseMessage() {
      return this.message.toUpperCase();
    },
    changeMessage() {
      this.message = 'No chance of plagiarism';
    },
    incrementCount() {
      this.count++;
    },
    // 4. Method to update the inputValue data property
    updateInputValue() {
      this.inputValue = 'Updated Value'
    },
    // 7a. Inline Handler
    handleClickInline() {
      alert('Inline click handler')
    },
    // 7b. Method Handlers
    handleClickMethod() {
      alert('Method click handler');
    },
     // 10. Components
    handleCustomEvent(data) {
      console.log(`Received custom event with data: ${data}`);
    },
  },

};
</script>
