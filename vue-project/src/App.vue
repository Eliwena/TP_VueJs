<script setup>
import Formik from "./components/Formik.vue";
import Field from "./components/Field.vue";
import Captcha from "./components/Captcha.vue";

import { ref } from "vue";


const isSubmitting = ref(true);

const initialValues = {
  email: "",
  username: "",
  description: "",
  ville: "",
  hobbies: false,
  captcha: "", 
};

const validate = (values) => {
  const errors = {};
  if (!values.email) {
    errors.email = "Required";
  } else if (
    !/^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i.test(values.email)
  ) {
    errors.email = "Invalid email address";
  }
  return errors;
};


const emit = defineEmits(["submit"]);

function onSubmit(errors) {
  if(errors.values.length === 0){
    emit("submit", {
      isSubmitting:false,
    });
  }
  console.log("eeeeee")
}


const options = [
  {
    id: 1,
    src: "https://picsum.photos/200?random=1",
  },
  {
    id: 2,
    src: "https://picsum.photos/200?random=2",
  },
  {
    id: 3,
    src: "https://picsum.photos/200?random=3",
  },
  {
    id: 4,
    src: "https://picsum.photos/200?random=4",
  },
  {
    id: 5,
    src: "https://picsum.photos/200?random=5",
  },
  {
    id: 6,
    src: "https://picsum.photos/200?random=6",
  },
  {
    id: 7,
    src: "https://picsum.photos/200?random=7",
  },
  {
    id: 8,
    src: "https://picsum.photos/200?random=8",
  },
  {
    id: 9,
    src: "https://picsum.photos/200?random=9",
  },
];

</script>

<template>
  <header>
    <div class="wrapper"></div>
  </header>
  <div>
    <h1>Formik</h1>
        <Formik :initialValues="initialValues" :validate="validate" @submit="onSubmit" >
          <form @submit.prevent="handleSubmit">
            <Field name="username" /> <!--Text--><br>
            <Field name="description" as="textarea"/> <!--Textarea--><br>
            <Field name="ville" as="select">
              <option value="Paris">Paris</option>
              <option value="Lyon">Lyon</option>
              <option value="Marseille">Marseille</option>
            </Field> <!--Select--><br>
            <Field name="hobbies" as="checkbox"/> <!--Checkbox--><br>
            <Field name="captcha" :as="Captcha" :options="options"/>
            <button type="submit" :disabled="!isSubmitting">Submit</button>
 
          </form>
        </Formik>
  </div>
  <main></main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
