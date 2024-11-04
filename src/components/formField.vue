<script setup>
import { Form } from 'vee-validate';
// import * as yup from 'yup';
</script>

<template>
    <main>
        <section class="router">
            Back
        </section>
        <section class="form_container">
            <div>
                <h1>Let’s get started</h1>
                <p>Enter your information just as it appears on your health insurance card or pay stub.</p>
                <p>*Required</p>
            </div>
            <Form action="">
                <div class="form_button">
                    <button>Next</button>
                </div>
            </Form>
        </section>
    </main>
</template>

<style scoped>
.form_button {
   width: 100%;
}
.form_button button {
     background: #5b2f91;
     color: #fff;
     widows: 100%;
}
</style>