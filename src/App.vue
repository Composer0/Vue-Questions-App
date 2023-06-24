<template>
  <div class="ctr">
    <div class="progress">
      <div 
        class="bar" 
        :style="{ width: `${ (questionsAnswered / questions.length) * 100}%` }"></div>
      <div class="status">
        {{ questionsAnswered }} out of {{ questions.length }} questions answered</div>
    </div>
    <transition name="fade" mode="out-in">
      <Questions
        v-if="questionsAnswered < questions.length"
        :questions="questions"
        :questionsAnswered="questionsAnswered"
        @question-answered="questionAnswered"
      />
  
      <Results 
      v-else
      :results="results" 
      :totalCorrect="totalCorrect"
      />
  </transition>
  
    <button 
    type="button" 
    class="reset-btn" 
    @click.prevent="reset" 
    v-if="this.questionsAnswered === questions.length"
  >
    Reset
  </button>
  <a 
    class="reset-btn"
    v-if="questionsAnswered === questions.length && totalCorrect >= 3"
    href="https://www.orionpalmer.com"
    target="_blank"
  >
    Return to Portfolio
  </a>
  <a 
    class="reset-btn"
    v-if="questionsAnswered === questions.length && totalCorrect < 3"
    href="https://studentprivacy.ed.gov/sites/default/files/resource_document/file/A%20parent%20guide%20to%20ferpa_508.pdf#:~:text=Under%20FERPA%2C%20a%20parent%20has%20the%20right%20to,in%20violation%20of%20the%20child%E2%80%99s%20rights%20of%20privacy."
    target="_blank"
  >
    FERPA Handbook
  </a>
  </div>
</template>

<script>

import Questions from './components/Questions.vue';
import Results from './components/Results.vue';
export default {
  name: 'App',
  components: {
    Questions,
    Results
  },
  data() {
    return {
      questionsAnswered: 0,
      totalCorrect: 0,
      questions: [
          {
              q: 'Which piece of federal legislation protects confidentiality of student records?', 
              answers: [
                  {
                    text: 'McKinney-Vento',
                    is_correct: false
                  },
                  {
                    text: 'Individuals with Disabilities Education Act (IDEA)',
                    is_correct: false 
                  },
                  {
                    text: 'Section 504 of the Rehabilitation Act',
                    is_correct: false 
                  },
                  {
                    text: 'Family Educational Rights and Privacy Acto of 1974 (FERPA)',
                    is_correct: true 
                  }
              ] 
          },
          { 
              q: 'Which of the following information from school records may be shared without obtaining written permission?', 
              answers: [
                  {
                    text: 'birthday',
                    is_correct: true
                  },
                  {
                    text: 'grades',
                    is_correct: false 
                  },
                  {
                    text: 'test scores',
                    is_correct: false 
                  },
                  {
                    text: 'placement in special services',
                    is_correct: false 
                  }
              ] 
          },
          { 
              q: "If a parent believes that information in their minor child's school records is inaccurate, which of the following options is available?", 
              answers: [
                  {
                    text: "The parent may seek an amendment or correction of their child's education records.",
                    is_correct: true
                  },
                  {
                    text: 'The parent does not have any rights to access student records.',
                    is_correct: false 
                  },
                  {
                    text: "Parents may remove portions of the student's record.",
                    is_correct: false 
                  },
                  {
                    text: "Schools must change the disputed information.",
                    is_correct: false
                  }
              ] 
          },
      ],
      results: [
          {
              min: 0,
              max: 2,
              title: "Try again!",
              desc: "Please review the FERPA Handbook for review and please try again."
          },
          {
              min: 3,
              max: 3,
              title: "Congratulations!",
              desc: "Congratulations you have passed the FERPA quiz!"
          }
      ]
    }
  },
  methods: {
    questionAnswered(is_correct) {
      if(is_correct) {
        this.totalCorrect++;
      }

      this.questionsAnswered++
    },
    reset() {
      this.questionsAnswered = 0;
      this.totalCorrect = 0;
    }
  }
}
</script>

<style>


</style>
