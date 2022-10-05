<template>
    <div class="form-group">
        <h3>Eigen risico</h3>
        <div class="form-input my-4">
            <div class="input__group">
                <label class="input__title">
                    Kies de hoogste van het eigen risico
                </label>
                <select class="form-control" :class="disabled ? 'disabled' : ''" :disabled="disabled"
                    @input="$emit('update:deductible', $event.target.value)">
                    <option value="385">
                        € 385 - verplicht eigen risico
                    </option>
                    <option value="885">
                        € 885 - korting van € 22 per jaar
                    </option>
                </select>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'RegistrationReason',
    props: {
        disabled: Boolean,
    },
}
</script>

<style scoped>
.form-control:disabled,
.form-select:disabled {
    color: grey;
}
</style>
