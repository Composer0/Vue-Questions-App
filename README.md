# FERPA Quiz Vue

This template should help get you started developing with Vue 3 in Vite.

Demo - [https://harmonious-lokum-1ab6cc.netlify.app/](https://ferpa-quiz-vue.netlify.app/)

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```


---

# FERPA Quiz Application Documentation

The FERPA Quiz application is a Vue.js-based interactive quiz that tests the user's knowledge of the Family Educational Rights and Privacy Act (FERPA). It allows users to answer a series of multiple-choice questions related to FERPA regulations and provides instant feedback on their answers. The application consists of three main components: `App`, `Questions`, and `Results`.

## App Component

The `App` component serves as the main entry point for the FERPA Quiz application. It manages the overall flow of the quiz, tracks the user's progress, and displays the appropriate content based on user interactions.

### Data Properties

- `questionsAnswered`: Tracks the number of questions answered by the user.
- `totalCorrect`: Tracks the total number of correct answers given by the user.
- `questions`: An array of question objects, each containing a question prompt and an array of answer choices. Each answer choice includes text and a flag indicating if it's correct.

### Methods

- `questionAnswered(is_correct)`: A method triggered when a question is answered. It updates the `totalCorrect` counter if the answer is correct and increments the `questionsAnswered` counter.

- `reset()`: A method to reset the quiz by setting `questionsAnswered` and `totalCorrect` back to zero.

### Components

- `<Questions>`: A component that renders the questions to the user. It accepts the `questions` array, `questionsAnswered`, and `@question-answered` event to update the parent's counters.

- `<Results>`: A dynamic component that displays feedback to the user based on their quiz performance. It takes `results` and `totalCorrect` props to determine the appropriate feedback message to display.

## Questions Component

The `Questions` component is responsible for rendering the questions and answer choices to the user and collecting their responses.

### Props

- `questions`: An array of question objects, each containing the question prompt and answer choices.
- `questionsAnswered`: The number of questions the user has already answered.

### Events

- `@question-answered`: An event emitted when a question is answered. It sends a boolean value indicating if the answer is correct.

### Methods

- `answerQuestion(answer)`: A method triggered when an answer choice is clicked. It emits the `@question-answered` event with the correctness of the answer.

## Results Component

The `Results` component provides personalized feedback to the user based on their quiz performance.

### Props

- `results`: An array of objects, each representing feedback messages based on user performance.
- `totalCorrect`: The total number of correct answers given by the user.

### Computed Property

- `resultIndex`: Calculates the index of the feedback message to display based on the `results` array and `totalCorrect`.

## Conclusion

The FERPA Quiz application is a comprehensive educational tool that tests users' knowledge of FERPA regulations. Through its structured components, dynamic feedback, and user-friendly interface, the application provides an engaging experience for users to learn and assess their understanding of student privacy rights under FERPA.

---

The FERPA Quiz application showcases Vue.js's versatility in building interactive and educational web applications. Its component-based architecture, event handling, and dynamic feedback mechanism contribute to a seamless and informative quiz-taking experience for users.
