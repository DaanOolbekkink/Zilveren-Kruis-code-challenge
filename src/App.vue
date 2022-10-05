<template>
    <div id="app" class="main-placeholder">
        <!-- HEADER -->
        <DefaultHeader></DefaultHeader>

        <!-- CONTENT HERE -->
        <RegistrationForm></RegistrationForm>

        <!-- FOOTER -->
        <DefaultFooter></DefaultFooter>
    </div>
</template>

<script>
import RegistrationForm from './components/RegistrationForm';
import DefaultHeader from './components/DefaultHeader';
import DefaultFooter from './components/DefaultFooter.vue';

export default {
    name: 'App',
    components: {
        RegistrationForm: RegistrationForm,
        DefaultHeader: DefaultHeader,
        DefaultFooter: DefaultFooter,
    },
};
</script>

<style lang="scss">

</style>
