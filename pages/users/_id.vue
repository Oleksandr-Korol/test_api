<template>
    <section>
        <h1>  {{user.name}}
        </h1>
        <hr>
        <h3>
            {{user.email}}
        </h3>
    </section>
</template>

//валідація вхідних параметрів, на  цій сторінці ми має приймати динамічний параметр 

<script>
export default {
    validate({params}){
        return /^\d+$/.test(params.id)
    },
    async asyncData ({$axios, params}){
         const user = await $axios.$get('http://tlutsysh.pythonanywhere.com/api/v1/user/' + params.id)
        return {user}
    }
}
</script>