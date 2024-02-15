<script>
export default {
    data() {
        return {
            firstName: this.firstName,
            lastName: this.lastName,
            birthdate: this.birthdate,
            username: this.username,
            description: this.description,
            password: this.password,
            confirmPassword: this.confirmPassword,
        };
    },
    methods: {
        submitForm() {
            if (this.password != this.confirmPassword) {
                alert("Les mots de passe ne sont pas identiques");
                return;
            }
            const formData = {
                firstName: this.firstName,
                lastName: this.lastName,
                birthdate: this.birthdate,
                username: this.username,
                description: this.description,
                password: this.password
            };
            alert(`Formulaire soumis avec succès!\n\nRésumé:\nPrénom: ${formData.firstName}\nNom: ${formData.lastName}\nDate de naissance: ${formData.birthdate}\nPseudo: ${formData.username}\nDescription: ${formData.description}`);
            
        }
    }
};
</script>

<template>
    <div class="register-form">
        <h2>Formulaire d'inscription</h2>
        <form @submit.prevent="submitForm">
            <div>
                <label for="first_name">Prénom:</label>
                <input type="text" id="first_name" v-model="firstName" required>
            </div>
            <div>
                <label for="last_name">Nom:</label>
                <input type="text" id="last_name" v-model="lastName" required>
            </div>
            <div>
                <label for="birthdate">Date de naissance:</label>
                <input type="date" id="birthdate" v-model="birthdate" required>
            </div>
            <div>
                <label for="username">Pseudo:</label>
                <input type="text" id="username" v-model="username" required>
            </div>
            <div>
                <label for="description">Description:</label>
                <textarea id="description" v-model="description" rows="4"></textarea>
            </div>
            <div>
                <label>Niveau en Vue.js:</label>
                <select v-model="vueLevel">
                    <option value="Débutant">Débutant</option>
                    <option value="Intermédiaire">Intermédiaire</option>
                    <option value="Confirmé">Confirmé</option>
                </select>
            </div>
            <div class="like-vue">
                <label>Aimez-vous Vue.js ?</label>
                <div>
                    <input type="radio" id="oui" value="oui" v-model="likeVue" name="likeVue">
                    <label for="oui">Oui</label>
                    <input type="radio" id="non" value="non" v-model="likeVue" name="likeVue">
                    <label for="non">Non</label>
                </div>
            </div>
            <div>
                <label for="password">Mot de passe:</label>
                <input type="password" id="password" v-model="password" required>
            </div>
            <div>
                <label for="confirm_password">Confirmer le mot de passe:</label>
                <input type="password" id="confirm_password" v-model="confirmPassword" required>
            </div>

            <button type="submit">S'inscrire</button>

        </form>
    </div>
</template>

<style scoped>
.register-form {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f9f9f9;
}

.register-form h2 {
    text-align: center;
    margin-bottom: 20px;
    color: black;
}

.register-form label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
    color: black;
}

.register-form input[type="text"],
.register-form input[type="password"],
.register-form textarea,
.register-form input[type="date"] {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #007bff;
    border-radius: 5px;
    box-sizing: border-box;
}

.register-form button {
    width: 100%;
    padding: 10px;
    margin-top: 10px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

.register-form button:hover {
    background-color: #0056b3;
}

.error-message {
    color: red;
}

.register-form select {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-sizing: border-box;
}

.like-vue label {
    display: inline-block;
    margin-right: 10px;
}
</style>
