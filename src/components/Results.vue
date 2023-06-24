
<template>
    <div class="result">
        <div class="title">
            {{ results[resultIndex].title }}
        </div>
        <div class="desc">
            {{ results[resultIndex].desc }}
        </div>
    </div>
</template>

<script>
export default {
    props: [ "results", "totalCorrect" ],
    // computed property saves on results and time because we are also taking into account whether or not the user is answered the questions incorrect. If incorrect, then Vue does not update.
    computed: {
        resultIndex() {
            let index = 0;

            this.results.forEach((e, i) => {
                if( e.min <= this.totalCorrect && e.max >= this.totalCorrect ){
                    index = i;
                }
            });
            return index;
        },
    }
}
</script>
