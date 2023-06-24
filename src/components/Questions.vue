<template>
    <div class="questions-ctr" key="questions">
    <transition-group name="fade">
        <div 
            class="single-question" 
            v-for="(question, qi) in questions" 
            :key="question.q" 
            v-show="questionsAnswered === qi"
        >
        <!-- v-show is more performant. -->
            <div class="question">{{ question.q }}</div>
            <div class="answers">
                <div 
                    class="answer" 
                    v-for="answer in question.answers" 
                    :key="answer.text" 
                    @click.prevent="selectAnswer(answer.is_correct)"
                >
                    {{ answer.text }}
                </div>
            </div>
        </div>
    </transition-group>
    </div>
      
</template>

<script>
export default {
    props: ["questions", "questionsAnswered"],
    emits: ['question-answered'],
    methods: {
        selectAnswer(is_correct) {
            this.$emit('question-answered', is_correct);
        }
    }
}
</script>