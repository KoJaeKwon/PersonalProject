<template>
    <div>
        <h3>Board Modified Form</h3>
        <form @submit.prevent="onSubmit">
            <table>
                <tr>
                    <td>글번호</td>
                    <td><input type="text" :value="board.boardNo" disabled></td>
                </tr>
                <tr>
                    <td>등록일자</td>
                    <td><input type="text" :value="board.regDate" disabled></td>
                </tr>
                <tr>
                    <td>제목</td>
                    <td><input type="text" v-model="title"></td>
                </tr>
                <tr>
                    <td>작성자</td>
                    <td><input type="text" :value="board.writer" disabled></td>
                </tr>
                <tr>
                    <td>내용</td>
                    <td><textarea cols="50" rows="20" v-model="content"></textarea></td>
                </tr>
            </table>

            <div>
                <button type="submit">수정 완료</button>
                <router-link :to="{ name: 'BoardReadPage', params: { boardNo: board.boardNo.toString() } }">
                    취소
                </router-link>
            </div>
        </form>
    </div>
</template>

<script>
export default {
    name: 'BoardModifyForm',
    props: {
        board: {
            type: Object,
            required: true
        }
    },
    data () {
        return {
            title: '',
            content: ''
        }
    },
    methods: {
        onSubmit () {
            const { content } = this
            this.$emit('submit', {  content })
        }
    },
    created () {
        this.content = this.board.content
    }
}
</script>