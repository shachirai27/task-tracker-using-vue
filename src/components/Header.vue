<template>
    <header>
        <h1>{{title}}</h1>
        <Button @btn-click="$emit('toggle-add-task')" 
        :btntext="showAddTask ? 'Close' : 'Add Task'" 
        :btnColor="showAddTask ? '#9a0000' : 'Green'" />
        <!-- <Button btntext="Update Task" btnColor="#76549A"/>
        <Button btntext="Delete Task" btnColor="#DF7861"/> -->
    </header>
</template>

<script>
import Button from './Button'

export default {
    
    name: 'HeaderComp',
    props: {
        title: {
            type:String,
            default: 'Hello World'
        },
        showAddTask: Boolean
    },
    components: {
    Button
}
}

</script>

<style scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>