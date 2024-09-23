<script>
    export let value = '';
    export let error = '';
</script>

<div class="form-field">
    <label for="message">Message*</label>
    <textarea id="message" bind:value={value} required></textarea>
    {#if error}
        <div class="error-message">{error}</div>
    {/if}
</div>




<style>

    .required-text {
        color: #797EA3;
        font-size: 15px;
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
        height: 23px;
    }
    .form-group {
        display: flex;
        align-items: center;
        margin-bottom: 2rem;
    }
</style>
