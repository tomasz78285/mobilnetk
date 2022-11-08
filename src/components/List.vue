<template>
    <table>
        <thead>
            <tr>
                <td>Name</td>
                <td>Code</td>
                <td>Country</td>
            </tr>
        </thead>
        <tbody>
            <tr v-for="it in italy" :key="it.id">
                <td>{{ it.name }}</td>
                <td>{{ it.code }}</td>
                <td>{{ it.country }}</td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    name: "list",
    data() {
        return {
            italy: []
        };
    },
    created() {
        fetch("http://localhost:3000/italy")
        .then(response => {
            return response.json();
        })
        .then(data => {
            this.italy = data;
        });
    }
};
</script>

<style>
</style>