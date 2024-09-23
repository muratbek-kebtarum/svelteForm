<script>
    import Form from "../lib/Form.svelte";
</script>

<div class="wrapper">
    <h1 class="title">Hello</h1>
    <div class="container">
        <form class="form">
            <p class="main-text">For business enquiries please <br> use the form below</p>
            <p class="required-text">*Required</p>
            <Form/>
        </form>
    </div>
</div>

<style>
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
