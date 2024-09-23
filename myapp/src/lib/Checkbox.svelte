<script>
    export let checked = false;
    export let error = '';
</script>
<div class="form-group">
    <label class="checkbox-field">
        <input type="checkbox" bind:checked={checked} />
        <span class="checkmark"></span>
        <span>I accept <a href="#">Terms and Privacy Policy</a></span>
    </label>
    {#if error}
        <br>
        <div class="error-message">{error}</div>
    {/if}
</div>

<style>
    .error-message {
        color: #FF6347; /* Change this to your desired color, e.g., Tomato */
        font-size: 0.8rem;
        margin-top: 0.2rem;
    }
    .form-group {
        display: flex;
        align-items: center;
        margin-bottom: 2rem;
    }

    .checkbox-field {
        display: flex;
        align-items: center;
        font-size: 15px;
        color: #797EA3;
        border-radius: 4px; /* Скругление углов */

    }
    .checkbox-field:hover {
        border-color: #142eea; /* Change border color on hover */
    }

    .checkbox-field input[type="checkbox"] {
        position: absolute;
        opacity: 0;
        cursor: pointer;
    }

    .checkbox-field .checkmark {
        width: 5px;
        height: 5px;
        background-color: #1a1d30;
        border-radius: 8px;
        display: inline-block;
        margin-right: 0.75rem;
        position: relative;
        transition: background-color 0.3s ease;
        border: 2px solid #3F4363; /* Граница вокруг чекбокса */
        padding: 0.7rem; /* Отступ внутри границы */
    }

    .checkbox-field .checkmark:hover {
        border-color: #8F94B8CC; /* Change border color on hover */
    }

    .checkbox-field input:checked + .checkmark {
        background-color: #2C2F47;
        border: 2px solid #2C2F47; /* Граница вокруг чекбокса */
    }

    .checkbox-field .checkmark:after {
        content: "";
        position: absolute;
        display: none;
    }

    .checkbox-field input:checked + .checkmark:after {
        display: block;
    }

    .checkbox-field .checkmark:after {
        left: 8px;
        top: 4px;
        width: 7px;
        height: 12px;
        border: solid white;
        border-width: 0 2px 2px 0;
        transform: rotate(45deg);
    }

    .checkbox-field a {
        color: rgba(255, 255, 255, 0.7);
        text-decoration: none;
        border-bottom: 1px solid rgba(255, 255, 255, 0.7);
        transition: color 0.3s ease, border-bottom-color 0.3s ease;
    }

    .checkbox-field a:hover {
        color: #fff;
        border-bottom-color: #2C2F47;
    }

    /*padding: 5px 0px 0px 0px;*/
    /*gap: 10px;*/
    /*border-radius: 8px 0px 0px 0px;*/
    /*opacity: 0px;*/

</style>
