<template>
    <form>
        <div class="container my-3">
            <div class="row">
                <div class="col-8">
                    <h1>Aanmelden</h1>

                    <h2>Gegevens</h2>
                    <RegistrationReason :reason="form.reason" @update:reason="v => form.reason = v"
                        :options="reasonOptions"></RegistrationReason>

                    <RegistrationPersonalInformation :firstName="form.name.firstName"
                        @update:firstName="v => form.name.firstName = v" :lastName="form.name.lastName"
                        @update:lastName="v => form.name.lastName = v" :prefix="form.name.prefix"
                        @update:prefix="v => form.name.prefix = v" :dateOfBirth="form.dateOfBirth"
                        @update:dateOfBirth="v => form.dateOfBirth = v" :bsn="form.bsn" @update:bsn="v => form.bsn = v"
                        @update:sex="v => form.sex = v">
                    </RegistrationPersonalInformation>

                    <h2 class="mt-5">Verzekering</h2>
                    <RegistrationBasicinsurance @update:basicinsurance="v => form.basicinsurance = v"
                        @update:paymentTerm="v => form.paymentTerm = v"></RegistrationBasicinsurance>

                    <RegistrationDeductible :disabled="!form.basicinsurance" @update:deductible="v => form.deductible = v">
                    </RegistrationDeductible>
                    <RegistrationAdditionalInsurance @update:additionalInsurance="v => form.additionalInsurance = v"
                        @update:additionalDentalInsurance="v => form.additionalDentalInsurance = v">
                    </RegistrationAdditionalInsurance>

                    <h2 class="mt-5">Controleren</h2>
                    <div class="form-group">
                        <h3>Gekozen pakket</h3>
                        <h3 v-if="form.name.firstName">{{form.name.firstName[0]}}. {{form.name.prefix}}
                            {{form.name.lastName}} <span v-if="form.dateOfBirth">({{form.dateOfBirth | date('dd-MM-yyyy')}})</span></h3>
                            <div class="ratingbar">
                                <p class="bold">Basisverzekering</p>
                                <p>{{form.basicinsurance}}</p>
                            </div>
                            <div class="ratingbar">
                                <p class="bold">Eigen risico</p>
                            </div>
                            <div class="ratingbar">
                                <p class="bold">Aanvullende verzekering</p>
                            </div>
                    </div>
                    <div class="form-group">
                        <h3>Totaalpremie</h3>

                    </div>
                    <div class="form-group">
                        <h3>Adres en contactgegevens</h3>
                    </div>
                </div>
                <div class="col-4">
                    <div class="card card--filled-secondary h-auto">
                        <div class="card-body">
                            <div class="sf-contactblok-content">
                                <h3 class="mb-2">We staan voor je klaar</h3>
                                <p class="mb-5">
                                    Twijfel je? Heb je een vraag?
                                </p>
                                <div class="phonenumber mb-2">
                                    <a href="tel:0900 040 03 09">
                                        <span class="sr-only">
                                            Telefoonnummer
                                        </span>
                                        0900 040 03 09
                                    </a>
                                    <div class="popover__container ml-1">
                                        <button id="info-phone" type="button"
                                            class="btn popover__btn btn--popover btn-none">
                                            <span class="sr-only">
                                                Informatie weergeven
                                            </span>
                                        </button>
                                    </div>
                                </div>
                                <small>
                                    Open op maandag t/m vrijdag van 08:00 tot
                                    17:00
                                </small>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </form>
</template>

<script>
import RegistrationReason from './registrationForm/RegistrationReason.vue';
import RegistrationPersonalInformation from './registrationForm/RegistrationPersonalInformation.vue';
import RegistrationBasicinsurance from './registrationForm/RegistrationBasicinsurance.vue';
import RegistrationDeductible from './registrationForm/RegistrationDeductible.vue';
import RegistrationAdditionalInsurance from './registrationForm/RegistrationAdditionalInsurance.vue';
import { dateFilter } from "vue-date-fns";

export default {
    name: "RegistrationForm",
    components: { RegistrationReason, RegistrationPersonalInformation, RegistrationBasicinsurance, RegistrationDeductible, RegistrationAdditionalInsurance },
    filters: {
        date: dateFilter
    },
    data() {
        return {
            form: {
                reason: null,
                name: {
                    firstName: null,
                    lastName: null,
                    prefix: null
                },
                email: '',
                dateOfBirth: null,
                sex: null,
                bsn: null,
                basicinsurance: null,
                deductible: null,
                paymentTerm: 'per jaar',
                additionalInsurance: null,
                additionalDentalInsurance: null,
            },
            reasonOptions: [
                'Overstappen per 1-1-2023 naar Zilveren Kruis',
                'Nieuwe werkgever met collectiviteit bij Zilveren Kruis'
            ]
        }
    },
    beforeMount() {
        this.form.reason = this.reasonOptions[0];
    }
};
</script>

<style scoped>
 .bold {
    font-weight: bold;
 }

 .ratingbar {
    border-bottom: 2px solid #dcebf3;
    border-top: unset;
 }
</style>
