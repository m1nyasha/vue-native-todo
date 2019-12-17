<template>
    <view>
        <view class="todos">
            <view class="todos-item" v-for="(todo, index) in todos">
                <touchable-opacity
                    :style="{
                        backgroundColor: (todo.status) ? '#e3e3e3' : '#e67e22',
                        padding: 10,
                        marginBottom: 10,
                        borderRadius: 30,
                    }"
                    :on-press="() => setTodo(index)"
                >
                    <text
                        :style="{
                            fontSize: 20,
                            color: '#fff'
                        }"
                        :class="{success: todo.status}"
                    >
                        {{ todo.title }}
                    </text>
                </touchable-opacity>
            </view>
            <view class="add-todos">
                <text-input
                    :style="{
                        height: 40,
                        width: 100 + '%',
                        borderColor: '#2ecc71',
                        borderWidth: 2,
                        borderRadius: 30
                    }"
                    v-model="todo_text"
                />
                <touchable-opacity
                    :style="{
                        backgroundColor: '#2ecc71',
                        borderRadius: 30,
                        padding: 10,
                        marginTop: 10
                    }"
                    :on-press="() => addTodo()"
                >
                    <text
                        :style="{
                            color: '#fff'
                        }"
                    >Add</text>
                </touchable-opacity>
            </view>
        </view>
    </view>
</template>

<script>
    export default {
        data() {
            return {
                todos: [
                    {
                        title: 'Помыть посуду',
                        status: false
                    },
                    {
                        title: 'Убраться в комнате',
                        status: true
                    },
                    {
                        title: 'Поменять фон на рабочем столе',
                        status: false
                    }
                ],
                todo_text: ''
            }
        },
        methods: {
            setTodo(index) {
                this.todos[index].status = !this.todos[index].status;
            },
            addTodo() {
                this.todos.push({
                    title: this.todo_text,
                    status: false
                });
                this.todo_text = '';
            }
        }
    }
</script>

<style scoped>
    .todos {
        paddingLeft: 10;
        paddingRight: 10;
        marginTop: 20;
    }

    .todo {
        font-weight: bold;
        margin-top: 10px;
        text-transform: uppercase;
    }

    .add-todos {
        marginTop: 10;
        padding: 10;
    }

    .todos-item {

    }

    .success {
        color: #e3e3e3;
        textDecorationLine: line-through;
    }

</style>