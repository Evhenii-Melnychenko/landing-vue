<script setup>
    import { computed, reactive } from 'vue'
    import { useI18n } from 'vue-i18n'
    import useVuelidate from '@vuelidate/core'
    import { email, helpers, minLength, required } from '@vuelidate/validators'

    const { t } = useI18n({ useScope: 'global' })

    const form = reactive({
        firstName: '',
        lastName: '',
        phone: '',
        email: '',
        service: '',
        message: '',
    })

    const rules = computed(() => ({
        firstName: {
            required: helpers.withMessage(() => t('contact.validation.required'), required),
            minLength: helpers.withMessage(() => t('contact.validation.min_name'), minLength(2)),
        },
        lastName: {
            required: helpers.withMessage(() => t('contact.validation.required'), required),
            minLength: helpers.withMessage(() => t('contact.validation.min_name'), minLength(2)),
        },
        phone: {
            required: helpers.withMessage(() => t('contact.validation.required'), required),
            minLength: helpers.withMessage(() => t('contact.validation.min_phone'), minLength(6)),
        },
        email: {
            required: helpers.withMessage(() => t('contact.validation.required'), required),
            email: helpers.withMessage(() => t('contact.validation.invalid_email'), email),
        },
    }))

    const v$ = useVuelidate(rules, form)

    async function submitForm() {
        const isValid = await v$.value.$validate()
        if (!isValid) return

        console.log(t('contact.validation.submit_success'))

        form.firstName = ''
        form.lastName = ''
        form.phone = ''
        form.email = ''
        form.service = ''
        form.message = ''
        v$.value.$reset()
    }
</script>

<template>
    <section class="contact" id="contact">
        <div class="container">
            <div class="contact-wrapper">
                <div class="contact-header">
                    <h2>{{ t('contact.title') }}</h2>
                    <p>{{ t('contact.description') }}</p>
                </div>
                
                <div class="contact-main">
                    <div class="contact-form">
                        <h3>{{ t('contact.form_title') }}</h3>
                        <form @submit.prevent="submitForm" novalidate>
                            <div class="form-row">
                                <div class="form-group">
                                    <label for="firstName">{{ t('contact.first_name') }} *</label>
                                    <input
                                      type="text"
                                      id="firstName"
                                      name="firstName"
                                      v-model.trim="form.firstName"
                                      :class="{ invalid: v$.firstName.$error }"
                                      @blur="v$.firstName.$touch()"
                                    >
                                    <small v-if="v$.firstName.$error" class="field-error">{{ v$.firstName.$errors[0].$message }}</small>
                                </div>
                                <div class="form-group">
                                    <label for="lastName">{{ t('contact.last_name') }} *</label>
                                    <input
                                      type="text"
                                      id="lastName"
                                      name="lastName"
                                      v-model.trim="form.lastName"
                                      :class="{ invalid: v$.lastName.$error }"
                                      @blur="v$.lastName.$touch()"
                                    >
                                    <small v-if="v$.lastName.$error" class="field-error">{{ v$.lastName.$errors[0].$message }}</small>
                                </div>
                            </div>
                            
                            <div class="form-row">
                                <div class="form-group">
                                    <label for="phone">{{ t('contact.phone_number') }} *</label>
                                    <input
                                      type="tel"
                                      id="phone"
                                      name="phone"
                                      v-model.trim="form.phone"
                                      :class="{ invalid: v$.phone.$error }"
                                      @blur="v$.phone.$touch()"
                                    >
                                    <small v-if="v$.phone.$error" class="field-error">{{ v$.phone.$errors[0].$message }}</small>
                                </div>
                                <div class="form-group">
                                    <label for="email">{{ t('contact.email_address') }} *</label>
                                    <input
                                      type="email"
                                      id="email"
                                      name="email"
                                      v-model.trim="form.email"
                                      :class="{ invalid: v$.email.$error }"
                                      @blur="v$.email.$touch()"
                                    >
                                    <small v-if="v$.email.$error" class="field-error">{{ v$.email.$errors[0].$message }}</small>
                                </div>
                            </div>
                            
                            <div class="form-group">
                                <label for="service">{{ t('contact.topic') }}</label>
                                <select id="service" name="service" v-model="form.service">
                                    <option value="">{{ t('contact.select_topic') }}</option>
                                    <option value="option1">{{ t('contact.option1') }}</option>
                                    <option value="option2">{{ t('contact.option2') }}</option>
                                    <option value="option3">{{ t('contact.option3') }}</option>
                                    <option value="option4">{{ t('contact.option4') }}</option>
                                    <option value="option5">{{ t('contact.option5') }}</option>
                                    <option value="option6">{{ t('contact.option6') }}</option>
                                    <option value="other">{{ t('contact.other') }}</option>
                                </select>
                            </div>
                            
                            <div class="form-group">
                                <label for="message">{{ t('contact.your_message') }}</label>
                                <textarea id="message" name="message" v-model.trim="form.message" :placeholder="t('contact.enter_your_message')"></textarea>
                            </div>
                            
                            <button type="submit" class="submit-btn">{{ t('contact.send') }}</button>
                        </form>
                    </div>
                    
                    <div class="contact-info">
                        <div class="contact-item">
                            <div class="contact-icon">
                                <i class="pi pi-map-marker"></i>
                            </div>
                            <h3>{{ t('contact.visit_our_office') }}</h3>
                            <p>{{ t('contact.address_placeholder') }}</p>
                        </div>
                        
                        <div class="contact-item">
                            <div class="contact-icon">
                                <i class="pi pi-phone"></i>
                            </div>
                            <h3>{{ t('contact.call_us_today') }}</h3>
                            <p><a href="tel:123456789">{{ t('contact.phone_number_placeholder') }}</a></p>
                        </div>
                        
                        <div class="contact-item">
                            <div class="contact-icon">
                                <i class="pi pi-envelope"></i>
                            </div>
                            <h3>{{ t('contact.email_us') }}</h3>
                            <p><a href="mailto:name@gmail.com">name@gmail.com</a></p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>

.contact {
    background: var(--color-white);
    padding: 100px 0;
    position: relative;

    &::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="20" cy="20" r="1" fill="rgba(0,87,27,0.05)"/><circle cx="80" cy="80" r="1" fill="rgba(0,87,27,0.05)"/></svg>') repeat;
        opacity: 0.6;
    }
}
        
.contact-wrapper {
    position: relative;
    z-index: 2;
}
        
.contact-header {
    text-align: center;
    margin-bottom: 60px;

    h2 {
        font-size: 3rem;
        color: var( --color-primary);
        margin-bottom: 20px;
        font-weight: 700;
    }

    .contact-header p {
        font-size: 1.3rem;
        color: #333333;
        opacity: 0.9;
    }
}

.contact-main {
    display: grid;
    grid-template-columns: 2fr 1fr;
    gap: 60px;
    max-width: 1200px;
    margin: 0 auto;
}

.contact-form {
    background: var(--color-white);
    padding: 50px 40px;
    border-radius: 20px;
    box-shadow: 0 20px 60px rgba(0,87,27,0.1);
    border: 2px solid rgba(0,87,27,0.08);
    position: relative;
    overflow: hidden;

    &::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        height: 6px;
        background: linear-gradient(90deg, var( --color-primary), var( --color-primary-light));
        border-radius: 20px 20px 0 0;
    }
}
        
.contact-form h3 {
    font-size: 2rem;
    color: var( --color-primary);
    margin-bottom: 30px;
    font-weight: 700;
    text-align: center;
}
        
.form-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-bottom: 25px;
}

.form-group {
    margin-bottom: 25px;
}

.form-group label {
    display: block;
    font-weight: 600;
    color: var( --color-primary);
    margin-bottom: 8px;
    font-size: 1rem;
}
        
.form-group input,
.form-group select,
.form-group textarea {
    width: 100%;
    padding: 15px 20px;
    border: 2px solid #e1e5e9;
    border-radius: 12px;
    font-size: 1rem;
    color: #333333;
    background: var(--color-white);
    transition: all 0.3s ease;
    font-family: inherit;

    &:focus {
        outline: none;
        border-color: var( --color-primary);
        box-shadow: 0 0 0 3px rgba(0, 87, 27, 0.1);
        transform: translateY(-2px);
    }

    &:hover {
        border-color: var( --color-primary);
    }
}

.form-group input.invalid,
.form-group select.invalid,
.form-group textarea.invalid {
    border-color: var(--color-error);
    box-shadow: 0 0 0 3px rgba(255, 76, 76, 0.15);
}

.field-error {
    display: block;
    margin-top: 8px;
    color: var(--color-error);
    font-size: 0.85rem;
    font-weight: 600;
}

.form-group textarea {
    resize: vertical;
    min-height: 120px;
}

.form-group select {
    cursor: pointer;
    background-image: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="%2300571B"><path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd"/></svg>');
    background-repeat: no-repeat;
    background-position: right 15px center;
    background-size: 16px;
    appearance: none;
}
        
.submit-btn {
    width: 100%;
    padding: 18px 25px;
    background: linear-gradient(135deg, var( --color-primary) 0%, var( --color-primary-light) 100%);
    color: var(--color-white);
    border: none;
    border-radius: 50px;
    font-size: 1.2rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1px;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 8px 25px rgba(0,87,27,0.2);

    &:hover {
        transform: translateY(-3px);
        box-shadow: 0 12px 35px rgba(0,87,27,0.3);
        background: linear-gradient(135deg, var( --color-primary-light) 0%, var( --color-primary) 100%);
    }

    &:active {
        transform: translateY(-1px);
    }
}
  
.contact-info {
    display: flex;
    flex-direction: column;
    gap: 30px;
}

.contact-item {
    background: var(--color-white);
    padding: 35px 30px;
    border-radius: 15px;
    box-shadow: 0 10px 30px rgba(0,87,27,0.1);
    border-left: 5px solid var( --color-primary);
    transition: all 0.3s ease;
    text-align: center;

    &:hover {
        transform: translateY(-5px);
        box-shadow: 0 15px 40px rgba(0,87,27,0.15);
    }
}
        
.contact-icon {
    font-size: 2.5rem;
    margin-bottom: 15px;
    display: block;
}

.contact-item h3 {
    font-size: 1.3rem;
    color: var(--color-primary);
    margin-bottom: 12px;
    font-weight: 700;
}
        
.contact-item p {
    color: var(--color-secondary);
    font-size: 1.1rem;
    line-height: 1.6;
}

.contact-item a {
    color: var(--color-primary);
    text-decoration: none;
    font-weight: 600;
    transition: all 0.3s ease;
}

.contact-item a:hover {
    color: var( --color-primary-light);
    text-decoration: underline;
}

@media (max-width: 968px) {  
    .contact-main {
        grid-template-columns: 1fr;
        gap: 40px;
    }
    
    .form-row {
        grid-template-columns: 1fr;
        gap: 0;
    }
    
    .contact-form {
        padding: 30px 25px;
    }
}

@media (max-width: 575px) {
    .contact-header h2 {
        font-size: 2.2rem;
    }
    
    .contact-form h3 {
        font-size: 1.6rem;
    }
}

</style>