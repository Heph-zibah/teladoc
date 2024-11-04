<template>
    <main>
        <section><p>Back</p></section>
        <form @submit="onSubmit" class="registration-form">
            <h2 class="form-title">Let’s get started</h2>
            <p class="form-description">
            Enter your information just as it appears on your health insurance card or pay stub.
            </p>

            <div class="form-group">
            <label for="firstName" class="form-label">First Name*</label>
            <Field name="firstName" as="input" class="form-input" :class="{ 'input-error': errors.firstName }" />
            <ErrorMessage name="firstName" class="error-message" />
            </div>

            <div class="form-group">
            <label for="lastName" class="form-label">Last Name*</label>
            <Field name="lastName" as="input" class="form-input" :class="{ 'input-error': errors.lastName }" />
            <ErrorMessage name="lastName" class="error-message" />
            </div>

            <div class="form-group">
            <label for="email" class="form-label">Email*</label>
            <Field name="email" type="email" class="form-input" :class="{ 'input-error': errors.email }" />
            <ErrorMessage name="email" class="error-message" />
            </div>

            <div class="form-group">
            <label for="country" class="form-label">Country*</label>
            <Field name="country" as="select" class="form-select" :class="{ 'input-error': errors.country }">
                <option value="">Please Select</option>
                <option value="USA">United States Of America</option>
                <!-- Add other country options here -->
            </Field>
            <ErrorMessage name="country" class="error-message" />
            </div>

            <div class="form-group">
            <label for="zipCode" class="form-label">ZIP code*</label>
            <Field name="zipCode" type="number" placeholder="##### or #####-####" class="form-input" :class="{ 'input-error': errors.zipCode }" />
            <ErrorMessage name="zipCode" class="error-message" />
            </div>

            <div class="form-group">
            <label for="sex" class="form-label">Sex assigned at birth*</label>
            <Field name="sex" as="select" class="form-select" :class="{ 'input-error': errors.sex }">
                <option value="">Please Select</option>
                <option value="male">Male</option>
                <option value="female">Female</option>
            </Field>
            <ErrorMessage name="sex" class="error-message" />
            </div>

            <div class="form-group">
            <label for="dateOfBirth" class="form-label">Date Of Birth*</label>
            <Field name="dateOfBirth" type="text" placeholder="MM/DD/YYYY" class="form-input" :class="{ 'input-error': errors.dateOfBirth }" />
            <ErrorMessage name="dateOfBirth" class="error-message" />
            </div>

            <div class="form-group form-checkbox">
            <Field name="teladocCode" type="checkbox" class="checkbox-input" />
            <label for="teladocCode" class="checkbox-label">
                I received a Teladoc Health code from my employer or insurance company.
            </label>
            </div>

            <button type="submit" class="form-button">Next</button>
        </form>
    </main>
</template>

<script setup>
import { useForm, Field, ErrorMessage } from 'vee-validate'
import * as yup from 'yup'

const validationSchema = yup.object({
  firstName: yup.string().required('First Name is required'),
  lastName: yup.string().required('Last Name is required'),
  email: yup.string().email('Invalid email format').required('Email is required'),
  country: yup.string().required('Country is required'),
  zipCode: yup.number()
    .typeError('ZIP code must be a number')
    .positive('ZIP code must be a positive number')
    .integer('ZIP code must be an integer')
    .required('ZIP code is required'),
  sex: yup.string().required('Sex assigned at birth is required'),
  dateOfBirth: yup.date()
    .typeError('Invalid date format')
    .required('Date Of Birth is required'),
  teladocCode: yup.boolean(),
})

const { handleSubmit, errors } = useForm({
  validationSchema,
})

const onSubmit = handleSubmit(values => {
  console.log('Form Submitted:', values)
})
</script>

<style scoped>
.registration-form {
  max-width: 500px;
  margin: auto;
  padding: 20px;
  background-color: #fff;
}


.form-title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 10px;
  color: #333;
}


.form-description {
  font-size: 14px;
  color: #666;
  margin-bottom: 20px;
}


.form-group {
  margin-bottom: 15px;
}


.form-label {
  display: block;
  font-size: 14px;
  font-weight: 600;
  margin-bottom: 5px;
  color: #333;
}


.form-input,
.form-select {
  width: 100%;
  padding: 14px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 8px;
  color: #333;
}

.form-input {
  background-color: #fff; 
}


.form-input:focus {
  background-color: #fff;
}


.form-input:valid {
  background-color: #fff;
}

.error-message {
  font-size: 12px;
  color: red;
  margin-top: 5px;
}


.form-checkbox {
  display: flex;
  align-items: center;
}

.checkbox-input {
  margin-right: 10px;
}


.checkbox-label {
  font-size: 14px;
  color: #333;
}


.form-button {
  width: 100%;
  padding: 10px;
  background-color: #5b2f91;
  color: #fff;
  font-size: 16px;
  font-weight: 600;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.form-button:hover {
  background-color: #c9c0d8;
}

.input-error {
  border-color: red;
}
</style>
