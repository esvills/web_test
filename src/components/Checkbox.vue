<template>
    <label class="checkbox">
        <input type="checkbox" :value="value" @change="$emit('input', $event.target.checked)" />
        <span class="checkmark"></span>
    </label>
</template>

<script>
export default {
  name: 'checkbox',
  props: {
    value: {
      type: Boolean
    }
  }
}
</script>
<style scoped>
    .checkbox{
        display: inline-block;
        position: relative;
        margin-right: 25px;
        width: 28px;
        height: 28px;
        border: 4px solid #d7d7d7;
        border-radius: 8px;
        vertical-align: middle;
    }
    .checkbox input{
        display: none;
    }
    .checkmark{
        position: absolute;
        width: 100%;
        height: 100%;
        background: url("../assets/cheked.png") no-repeat center;
        opacity: 0;
    }
    .checkbox input:checked ~ .checkmark {
       opacity: 1;
    }
    /*input[type="checkbox"]+label::before,*/
    /*input[type="radio"]+label::before{*/
        /*content: "";*/
        /*position: absolute;*/
        /*top: 2px;*/
        /*left: 0;*/
        /*display: inline-block;*/
        /*margin: 0 5px 0 0;*/
        /**/
    /*}*/
    /*input[type="checkbox"]:checked+label::before {*/
        /*background: url("../assets/cheked.png") no-repeat center;*/
    /*}*/
</style>
