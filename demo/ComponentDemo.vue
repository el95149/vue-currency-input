<template>
  <div class="demo">
    <CurrencyInput
      v-model="value"
      :currency="currency"
      :locale="locale"
      :distraction-free="distractionFree"
      :min="min"
      :max="max"
      :validate-on-input="validateOnInput"
      class="demo__currency-input"/>
    <p>Raw number value: <code>{{ value != null ? value : 'null' }}</code></p>
    <hr>
    <h3>Options</h3>
    <div class="demo__options">
      <p>
        <label>
          <span>Distraction free</span>
          <input
            v-model="distractionFree"
            type="checkbox">
        </label>
      </p>
      <p>
        <label>
          <span>Currency</span>
          <select v-model="currency">
            <option value="EUR">EUR</option>
            <option value="USD">USD</option>
            <option value="JPY">JPY</option>
            <option value="GBP">GBP</option>
            <option value="BRL">BRL</option>
          </select>
        </label>
      </p>
      <p>
        <label>
          <span>Locale</span>
          <select v-model="locale">
            <option :value="undefined">auto</option>
            <option value="de">de</option>
            <option value="fr">fr</option>
            <option value="en">en</option>
            <option value="pt">pt</option>
            <option value="zh">zh</option>
          </select>
        </label>
      </p>
      <p>
        <label>
          <span>Min value</span>
          <input
            :max="max ? max : 10000"
            v-model.number="min"
            min="-10000"
            type="range">
        </label>
        <code v-if="min">{{ min }}</code>
      </p>
      <p>
        <label>
          <span>Max value</span>
          <input
            :min="min ? min : -10000"
            v-model.number="max"
            max="10000"
            type="range">
        </label>
        <code v-if="max">{{ max }}</code>
      </p>
      <p>
        <label>
          <span>Validate on input</span>
          <input
            v-model="validateOnInput"
            type="checkbox">
        </label>
      </p>
    </div>
  </div>
</template>

<script>

export default {
  name: 'ComponentDemo',
  data: () => ({
    value: 1234.5,
    currency: 'USD',
    locale: undefined,
    distractionFree: true,
    min: null,
    max: null,
    validateOnInput: false
  })
}
</script>

<style lang="scss" scoped>
.demo {
  font-family: "Segoe UI", Arial, sans-serif;
  line-height: 1.5;
  font-size: 14px;
  background-color: #f6f8fa;
  padding: 24px;
  margin-top: 16px;
}

.demo__options {
  p {
    display: flex;
    align-items: center;
    margin: 0 0 4px 0;
    height: 28px;

    code {
      margin-left: 8px;
    }
  }

  label {
    display: flex;
    align-items: center;
    font-size: 14px;

    & > span {
      display: inline-block;
      width: 120px;
    }
  }

  select, input {
    margin: 0;
    font-size: 14px;
  }
}

.demo__currency-input {
  font-size: 24px;
  padding: 8px 12px;
  max-width: 100%;
  box-sizing: border-box;
}
</style>
