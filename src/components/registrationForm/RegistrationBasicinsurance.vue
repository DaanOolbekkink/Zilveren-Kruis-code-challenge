<template>
    <div class="form-group">
        <h3>Basisverzekering</h3>
        <p>
            In Nederland is de basisverzekering verplicht.
            Iedereen wordt voor de basisverzekering
            geaccepteerd. De overheid bepaalt welke zorg hierin
            zit en dit is dus bij elke verzekeraar hetzelfde.
        </p>
        <div class="input__group">
            <label class="input__title">
                Kies uw basisverzekering
            </label>
            <div class="form-row">
                <div class="radio__tile">
                    <div class="radio custom-radio radio__option">
                        <input @input="$emit('update:basicinsurance', $event.target.value)" value="Basis Budget" type="radio"
                            name="radio-insurance" id="radio-insurance-basis-budget"
                            class="radio__input custom-control-input" />
                        <label for="radio-insurance-basis-budget" class="radio__label custom-control-label">
                            <p class="radio__description">
                                Basis Budget
                            </p>
                            <p class="radio__price">
                                € 1.393,26 per jaar
                            </p>
                        </label>
                    </div>
                </div>
                <div class="radio__tile radio__tile--choice">
                    <div class="badge radio__tile-badge">
                        Meest gekozen
                    </div>
                    <div class="radio custom-radio radio__option">
                        <input @input="$emit('update:basicinsurance', $event.target.value)" value="Basis Zeker" type="radio"
                            name="radio-insurance" id="radio-insurance-basis-zeker"
                            class="radio__input custom-control-input" />
                        <label for="radio-insurance-basis-zeker" class="radio__label custom-control-label">
                            <p class="radio__description">
                                Basis Zeker
                            </p>
                            <p class="radio__price">
                                € 1.483,54 per jaar
                            </p>
                        </label>
                    </div>
                </div>
                <div class="radio__tile">
                    <div class="radio custom-radio radio__option">
                        <input @input="$emit('update:basicinsurance', $event.target.value)"
                            value="Basis Exclusief (Restitutie)" type="radio" name="radio-insurance"
                            id="radio-insurance-basis-exclusief-(restitutie)"
                            class="radio__input custom-control-input" />
                        <label for="radio-insurance-basis-exclusief-(restitutie)"
                            class="radio__label custom-control-label">
                            <p class="radio__description">
                                Basis Exclusief (Restitutie)
                            </p>
                            <p class="radio__price">
                                € 1.624,62 per jaar
                            </p>
                        </label>
                    </div>
                </div>
            </div>
        </div>
        <div class="form-group">
            <div class="form-input my-4">
                <div class="input__group">
                    <label class="input__title">
                        Kies je betaaltermijn
                    </label>
                    <select class="form-control" @input="$emit('update:paymentTerm', $event.target.value)">
                        <option>per maand</option>
                        <option>per kwartaal</option>
                        <option selected>per jaar</option>
                    </select>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'RegistrationBasicinsurance'
}
</script>
