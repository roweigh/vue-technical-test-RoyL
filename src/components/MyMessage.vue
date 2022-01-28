<template>
    <div>
        <p @Click="highlight"> {{ msg }} </p>
        <button class="button" @click="deleteItem">Delete</button>
    </div>
</template>

<script>
    //MyMessage component that takes in a String as a property.
    export default {
        props: {
            msg: String
        },
        methods: {
            deleteItem() {
                //When the 'Delete' button is clicked, emits custom event to the parent component with message contents.
                this.$emit('deletedItem', this.msg);
            }
        },
    }
</script>
