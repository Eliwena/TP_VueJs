<script setup>
import Formik from "./components/Formik.vue";
import Field from "./components/Field.vue";
import Captcha from "./components/Captcha.vue";



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
    errors['email'] = "Email Required";
  } else if (!/^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i.test(values.email)) {
    errors['email'] = "Invalid email address";
  }
  if (!values.username) {
    errors['username'] = "Username Required";
  }else if (values.username.length < 5) {
  //username plus de 5 caeractères
    errors['username'] = "Username must be at least 5 characters";
  }
  if (!values.description) {
    errors['description'] = "Description Required";
  }
  return errors;
};


// const emit = defineEmits(["submit"]);

function onSubmit() {
  // if (errors.values.length === 0) {
  //   emit("submit", {
  //     isSubmitting: false,
  //   });
  // }
  alert("Formulaire envoyé");
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
  <div>
    <h1>Formik</h1>
    <!-- lister les errors -->

    <Formik :initialValues="initialValues" :validate="validate" @submit="onSubmit"
      v-slot="{ errors, handleSubmit, isSubmitting }">
      <div v-for="(error, key) in errors" :key="key">
        <h5>{{ error }}</h5>
      </div>
      <form @submit.prevent="handleSubmit">
        <Field name="email" type="email" /><br />
        <Field name="username" />
        <!--Text--><br />
        <Field name="description" as="textarea" />
        <!--Textarea--><br />
        <Field name="ville" as="select">
        </Field>
        <!--Select--><br />
        <Field name="hobbies" as="checkbox" />
        <!--Checkbox--><br />
        <Field name="captcha" :as="Captcha" :options="options" />
        <button type="submit">Submit</button>
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
