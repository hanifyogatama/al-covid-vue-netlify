<template>
<select 
    @change="onChange()" 
    v-model="selected" 
    class="form-select mt-10 block w-full boder p-3 rounded ml-10 mr-10">

    <option value="0">Select Country</option>
    <option v-for="country in countries" v-bind:key="country" :value="country.ID">
        {{ country.Country }}
    </option>
</select>
</template>

<script>
    export default {
        name: 'CountrySelect',
        props: ['countries'],
        data() {
            return{
                selected: 0
            }
        },
        methods: {
            onChange() {
                const country = this.countries.find((item) => item.ID === this.selected)

                this.$emit('get-country', country)
            }
        }
    }
</script>