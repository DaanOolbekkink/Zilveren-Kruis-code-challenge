<template>
    <div class="form-group">
        <h3>Reden van aanmelding</h3>
        <div class="form-input my-4">
            <label id="aanmeldreden-label" class="input__title">
                Wat is de reden van uw aanvraag?
            </label>
            <div class="input__group">
                <select class="form-control" :value="reason" @input="$emit('update:reason', $event.target.value)">
                    <option v-for="(option, key) in options" :key="key">
                        {{ option }}
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
        reason: String,
        options: Array,
    },
}
</script>
