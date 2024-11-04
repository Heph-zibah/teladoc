<template>
    <main class="registration-form">
        <a href="#" class="route-back"><img src="../assets/back-arrow-icon.png" alt="back arrow icon">Back</a>
        <form @submit.prevent="onSubmit" >
            <h2 class="form-title">Let’s get started</h2>
            <p class="form-description">
                Enter your information just as it appears on your health insurance card or pay stub.
            </p>

            <div class="form-group">
                <label :class="{ 'label-error': errors.firstName }" for="firstName" class="form-label">First Name*</label>
                <Field name="firstName" as="input" class="form-input" :class="{ 'input-error': errors.firstName }" />
                <ErrorMessage name="firstName" class="error-message" />
            </div>

            <div class="form-group">
                <label :class="{ 'label-error': errors.lastName }" for="lastName" class="form-label">Last Name*</label>
                <Field name="lastName" as="input" class="form-input" :class="{ 'input-error': errors.lastName }" />
                <ErrorMessage name="lastName" class="error-message" />
            </div>

            <div class="form-group">
                <label :class="{ 'label-error': errors.email }" for="email" class="form-label">Email*</label>
                <Field name="email" type="email" class="form-input" :class="{ 'input-error': errors.email }" />
                <ErrorMessage name="email" class="error-message" />
            </div>

            <div class="form-group">
                <label :class="{ 'label-error': errors.country }" for="country" class="form-label">Country*</label>
                <Field name="country" as="select" class="form-select" :class="{ 'input-error': errors.country }">
                    <option value="">Select</option>
                    <option value="USA">United States Of America</option>
                    <option value="CAN">Canada</option>
                    <option value="GBR">United Kingdom</option>
                    <option value="AUS">Australia</option>
                    <option value="DEU">Germany</option>
                    <option value="FRA">France</option>
                    <option value="ITA">Italy</option>
                    <option value="ESP">Spain</option>
                    <option value="MEX">Mexico</option>
                    <option value="BRA">Brazil</option>
                    <option value="IND">India</option>
                    <option value="CHN">China</option>
                    <option value="JPN">Japan</option>
                    <option value="RUS">Russia</option>
                    <option value="ZAF">South Africa</option>
                    <option value="NGA">Nigeria</option>
                    <option value="ARG">Argentina</option>
                    <option value="KOR">South Korea</option>
                    <option value="SGP">Singapore</option>
                    <option value="NZL">New Zealand</option>
                    <option value="NLD">Netherlands</option>
                    <option value="SWE">Sweden</option>
                </Field>
                <ErrorMessage name="country" class="error-message" />
            </div>

            <div class="form-group">
                <label :class="{ 'label-error': errors.zipCode }" for="zipCode" class="form-label">ZIP code*</label>
                <Field name="zipCode" type="number" placeholder="##### or #####-####" class="form-input" :class="{ 'input-error': errors.zipCode }" />
                <ErrorMessage name="zipCode" class="error-message" />
            </div>

            <div class="form-group">
                <label :class="{ 'label-error': errors.sex }" for="sex" class="form-label">Sex assigned at birth*</label>
                <Field name="sex" as="select" class="form-select" :class="{ 'input-error': errors.sex }">
                    <option value="">Select</option>
                    <option value="male">Male</option>
                    <option value="female">Female</option>
                    <option value="other">Other</option>
                </Field>
                <ErrorMessage name="sex" class="error-message" />
            </div>

            <div class="form-group">
                <label :class="{ 'label-error': errors.dateOfBirth }" for="dateOfBirth" class="form-label">Date Of Birth*</label>
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

const initialValues = {
  firstName: '',
  lastName: '',
  email: '',
  country: '',
  zipCode: '',
  sex: '',
  dateOfBirth: '',
  teladocCode: false,
}

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

const { handleSubmit, errors, resetForm } = useForm({
  initialValues,
  validationSchema,
})

const onSubmit = handleSubmit(values => {
  alert('Form has been submitted!')
  resetForm({ values: initialValues })
})
</script>

<style scoped>
.registration-form {
  max-width: 500px;
  margin: auto;
  padding: 20px;
  background-color: #fff;
}

.route-back {
    color: blue;
    display: flex;
    align-items: center;
    margin-bottom: 50px;
    font-weight: 700;
}

.route-back img {
    width: 18px;
    margin-right: 10px;
}

.form-title {
  font-size: 32px;
  font-weight: bold;
  margin-bottom: 10px;
  color: #333;
}

.form-description {
  font-size: 16px;
  color: #666;
  margin-bottom: 20px;
  line-height: 30px;
}

.form-group {
  margin-bottom: 17px;
}

.form-label {
  display: block;
  font-size: 14px;
  font-weight: 600;
  margin-bottom: 5px;
  color: #333;
}

.label-error {
  color: #d93025;
}

.form-input,
.form-select {
  width: 100%;
  padding: 14px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 8px;
  color: #333;
  background-color: #fff;
}

.form-input:focus {
  border-color: #5b2f91;
}

.input-error {
  border-color: #d93025;
  background-color: #fce8e6;
}

.error-message {
  display: flex;
  align-items: center;
  font-size: 12px;
  color: #000;
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
  padding: 14px;
  background-color: #5b2f91;
  color: #fff;
  font-size: 16px;
  font-weight: 600;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.form-button:hover {
  background-color: #ccc3d4;
}
</style>
