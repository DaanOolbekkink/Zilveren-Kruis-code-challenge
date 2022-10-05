<template>
    <div class="form-group">
        <h3>Persoonlijke gegevens</h3>
        <div class="form-input my-4">
            <div class="input__group">
                <label class="input__title">Naam</label>
                <input class="input__field form-control" type="text" :value="firstName"
                    @input="$emit('update:firstName', $event.target.value)" />
            </div>
        </div>
        <div class="form-input my-4">
            <div class="input__group">
                <label class="input__title">
                    Tussenvoegsels
                </label>
                <input class="input__field form-control" type="text" :value="prefix"
                    @input="$emit('update:prefix', $event.target.value)" />
            </div>
        </div>
        <div class="form-input my-4">
            <div class="input__group">
                <label class="input__title">Achternaam</label>
                <input class="input__field form-control" type="text" :value="lastName"
                    @input="$emit('update:lastName', $event.target.value)" />
            </div>
        </div>
        <div class="form-input my-4">
            <div class="input__group">
                <label class="input__title">Geslacht</label>
                <div class="form-row">
                    <div class="radio custom-radio radio__option">
                        <input @input="$emit('update:sex', $event.target.value)" value="man" id="man" class="radio__input custom-control-input" type="radio" name="geslacht" />
                        <label class="radio__label custom-control-label" for="man">
                            Man
                        </label>
                    </div>
                    <div class="radio custom-radio radio__option">
                        <input @input="$emit('update:sex', $event.target.value)" value="vrouw" id="vrouw" class="radio__input custom-control-input" type="radio" name="geslacht" />
                        <label class="radio__label custom-control-label" for="vrouw">
                            Vrouw
                        </label>
                    </div>
                </div>
            </div>
        </div>
        <div class="form-input my-4">
            <div class="input__group">
                <label class="input__title">
                    Geboortedatum
                </label>
                <DatePicker input-class="input__field form-control datepicker-form-control" :value="dateOfBirth"
                    @selected="emitDateOfBirth" :disabled-dates="disabledDates" :format="dateFormat"></DatePicker>
            </div>
        </div>
        <div class="form-input my-4">
            <div class="input__group">
                <label class="input__title">
                    Burgerservicenummer
                </label>
                <input class="input__field form-control" :class="!validBSN && bsnTyped ? 'is-invalid' : ''" type="text" :value="bsn"
                    @input="$emit('update:bsn', $event.target.value)" @blur="isValidBSN($event.target.value)" />
            </div>
            <div v-if="!validBSN && bsnTyped" class="input__feedback invalid-feedback mt-1"
                aria-live="polite">
                <span>Helaas is het ingevoerde
                    burgerservicenummer niet geldig. Probeer het
                    opnieuw.</span>
            </div>
        </div>
    </div>
</template>

<script>

import DatePicker from 'vuejs-datepicker';

export default {
    name: 'RegistrationRegistrationReason',
    components: { DatePicker },
    props: {
        firstName: String,
        prefix: String,
        lastName: String,
        dateOfBirth: Date,
        bsn: String,
    },
    data() {
        return {
            disabledDates: {
                from: ''
            },
            dateFormat: 'dd-MM-yyyy',
            validBSN: false,
            bsnTyped: false,
        }
    },
    beforeMount() {
        this.disabledDates.from = new Date()
    },
    methods: {
        emitDateOfBirth(value) {
            this.$emit('update:dateOfBirth', value)
        },
        isValidBSN(bsn) {
            this.bsnTyped = true;
            if (bsn.length < 8 || bsn.length > 9) {
                return false
            }

            const numbers = Array.from(String(bsn), Number)
            const lastNumber = numbers[numbers.length - 1]

            if (typeof lastNumber === 'number' && !numbers.includes(NaN)) {
                this.validBSN = !!(
                    (numbers
                        .slice(0, -1)
                        .reduce((a, b, i, arr) => b * (arr.length + 1 - i) + a, 0) -
                        lastNumber) %
                    11 ===
                    0
                )
            } else {
                this.validBSN = false;
            }
        },
        ComputeDigitAt(num, n) {
            return ((num / Math.pow(10, n - 1)) % 10) * n;
        }
    }
}
</script>

<style>
.vdp-datepicker input {
    width: 100%;
}

.datepicker-form-control[readonly] {
    background-color: unset;
}
</style>
