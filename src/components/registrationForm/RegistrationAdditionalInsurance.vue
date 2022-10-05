<template>
    <div>
        <div class="form-group">
            <h3>Aanvullende verzekering</h3>
            <p>
                Onze aanvullende verzekeringen kennen ruim 100
                verschillende vergoedingen. De hoogte van de
                vergoeding verschilt per pakket.hoogte van de
                vergoeding verschilt per pakket
            </p>
            <div class="form-input my-4">
                <div class="input__group">
                    <label class="input__title">
                        Kies uw aanvullende verzekering
                    </label>
                    <select class="form-control" @input="$emit('update:additionalInsurance', $event.target.value)">
                        <option selected>
                            Geen aanvullende verzekering
                            geselecteerd
                        </option>
                        <option>
                            Aanvullend 1 - € 21,38 per jaar
                        </option>
                        <option>
                            Aanvullend 2 - € 85,06 per jaar
                        </option>
                        <option>
                            Aanvullend 3 - € 198,63 per jaar
                        </option>
                        <option>
                            Aanvullend 4 - € 359,73 per jaar
                        </option>
                    </select>
                </div>
            </div>
        </div>
        <div class="form-group">
            <div class="form-input my-4">
                <div class="input__group">
                    <label class="input__title">
                        Kies uw tandartsverzekering
                    </label>
                    <select class="form-control" @input="$emit('update:additionalDentalInsurance', $event.target.value)">
                        <option selected>
                            Geen tandartsverzekering geselecteerd
                        </option>
                        <option>Tand 1 - € 80,28 per jaar</option>
                        <option>Tand 2 - € 221,65 per jaar</option>
                        <option>Tand 3 - € 449,36 per jaar</option>
                    </select>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'RegistrationReason'
}
</script>
