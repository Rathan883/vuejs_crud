<template>
    <div>
        <h2>Hello, {{  name }}</h2>
        <h2>{{  userData.name }}</h2>
        <h2>{{  userData.age }} </h2>
    </div>
</template>

<script>
export default {
    props: {
        name: {
            type: String, required: true },
            userData : {type: Object}
        }
    };
    </script>