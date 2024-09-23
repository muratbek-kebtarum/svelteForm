<script>
    import InputFieldName from "./InputFieldName.svelte";
    import InputFieldCompany from "./InputFieldCompany.svelte";
    import InputFieldEmail from "./InputFieldEmail.svelte";
    import InputFieldPhone from "./InputFieldPhone.svelte";
    import InputFieldSubject from "./InputFieldSubject.svelte";
    import InputFieldMessage from "./InputFieldMessage.svelte";
    import Checkbox from "./Checkbox.svelte";
    import SubmitButton from "./SubmitButton.svelte";
    import Loading from "./Loading.svelte";

    let showNotification = false;
    let loading = false;
    let errors = {
        name: '',
        company: '',
        email: '',
        phone: '',
        message: '',
        terms: ''
    };

    let formData = {
        name: '',
        company: '',
        email: '',
        phone: '',
        subject: '',
        message: '',
        acceptTerms: false
    };

    function validateEmail(email) {
        const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return re.test(String(email).toLowerCase());
    }

    function handlePhoneInput(event) {
        event.target.value = event.target.value.replace(/\D/g, '');
    }

    function validateForm() {
        let valid = true;

        if (!formData.name) {
            errors.name = 'Name is required';
            valid = false;
        } else {
            errors.name = '';
        }

        if (!formData.company) {
            errors.company = 'Company is required';
            valid = false;
        } else {
            errors.company = '';
        }

        if (!formData.email || !validateEmail(formData.email)) {
            errors.email = 'A valid email is required';
            valid = false;
        } else {
            errors.email = '';
        }

        if (formData.phone && formData.phone.length < 10) {
            errors.phone = 'Phone number should have at least 10 digits';
            valid = false;
        } else {
            errors.phone = '';
        }

        if (!formData.message) {
            errors.message = 'Message is required';
            valid = false;
        } else {
            errors.message = '';
        }

        if (!formData.acceptTerms) {
            errors.terms = 'You must accept the terms';
            valid = false;
        } else {
            errors.terms = '';
        }

        return valid;
    }
    function submitForm(event) {
        event.preventDefault();
        loading = true;

        if (validateForm()) {
            setTimeout(() => {
                showNotification = true;
                loading = false;

                formData = {
                    name: '',
                    company: '',
                    email: '',
                    phone: '',
                    subject: '',
                    message: '',
                    acceptTerms: false
                };

                setTimeout(() => (showNotification = false), 4000);
            }, 2000);
        } else {
            loading = false;
        }
    }

    function closeNotification() {
        showNotification = false;
    }

</script>

<style>
    .error-message {
        color: red;
        font-size: 0.8rem;
        margin-top: 0.2rem;
    }

    .notification {
        position: fixed;
        bottom: 20px;
        right: 20px;
        background-color: #4caf50;
        color: white;
        padding: 1rem;
        border-radius: 5px;
        z-index: 1000;
        cursor: pointer;
    }
     * {
         margin: 0;
         padding: 0;
         box-sizing: border-box;
     }



    .wrapper {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 100%;
        max-width: 500px;
    }

    .title {
        font-size: 55px;
        margin-bottom: 2rem;
        color: white;
    }

    .container {
        background-color: #171929;
        padding: 2rem;
        border-radius: 27px;
        width: 390px;
        text-align: center;
        padding: 40px 45px 40px 45px
    }

    .form p {
        margin-bottom: 1rem;
    }
    .main-text{
        color: white;
        font-size: 18px;
    }


    .form-field {
        margin-bottom: 1.5rem;
        text-align: left;
    }

    .form-field label {
        display: block;
        font-size: 0.9rem;
        margin-bottom: 0.5rem;
    }

    .form-field input,
    .form-field textarea {
        width: 100%;
        /*padding: 0.75rem;*/
        border-radius: 1px;
        border: none;
        background-color: #171929;
        border-bottom: 1px solid rgba(255, 255, 255, 0.3);
        color: #fff;
        font-size: 18px;
        outline: none;
    }

    /* Добавление эффектов при наведении и нажатии */
    .form-field input:hover,
    .form-field textarea:hover {
        border-bottom-color: #8F94B8; /* Подсветка при наведении */
    }

    .form-field input:active,
    .form-field textarea:active {
        border-bottom-color: #ffffff; /* Изменение цвета границы при нажатии */
    }
    .form-field:focus-within label {
        color: #ffffff; /* Цвет метки при фокусе на input */
    }

    .form-field input:focus,
    .form-field textarea:focus {
        border-bottom-color: #ffffff;
    }

    .form-field textarea {
        resize: none;
        height: 22px;
    }

</style>
<Loading loading={loading} />
<form on:submit={submitForm}>
    <InputFieldName bind:value={formData.name} error={errors.name} />
    <InputFieldCompany bind:value={formData.company} error={errors.company} />
    <InputFieldEmail bind:value={formData.email} error={errors.email} />
    <InputFieldPhone bind:value={formData.phone} on:input={handlePhoneInput} error={errors.phone} />
    <InputFieldSubject bind:value={formData.subject} error={errors.subject} />
    <InputFieldMessage bind:value={formData.message} error={errors.message} />
    <Checkbox bind:checked={formData.acceptTerms} error={errors.terms}/>
    <SubmitButton />
</form>

{#if showNotification}
    <div class="notification" on:click={closeNotification}>
        Data successfully submitted!
    </div>
{/if}
