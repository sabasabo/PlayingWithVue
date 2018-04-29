<template>
  <div>
    <h1> Your {{ myData }} is ready sir! </h1>
    <img v-if="isEmptyComment()" :src="myImg"/>
    <img v-else-if="isSmallComment()" :src="myImgSurprise"/>
    <img v-else :src="myImgShame"/>
    <div>
      <label>Your theComment:</label>
      <input @keypress.enter="addComment()" id="comment" v-model="theComment" placeholder="your theComment sir" type="text"/>
    </div>
      <comment-component v-for="comment in comments" :text="comment.text" :key="comment.id"></comment-component>
  </div>
</template>

<script>
import dogImg from '../assets/dog.jpg'
import dogImgSurprise from '../assets/dog-surprised.jpg'
import dogImgShame from '../assets/dog-shame.jpg'
import sound from '../assets/sound-portal.mp3'
import CommentComponent from './commentComponent'
export default {
  name: 'MyFirstComponent',
  components: {CommentComponent},
  data: () => ({
    myData: 'shitty page',
    myImg: dogImg,
    myImgSurprise: dogImgSurprise,
    myImgShame: dogImgShame,
    theComment: '',
    sound: sound,
    comments: []
  }),
  methods: {
    isEmptyComment () {
      return this.theComment.length === 0
    },
    isSmallComment () {
      return this.theComment.length < 4
    },
    playSound () {
      let audio = new Audio(sound)
      audio.play()
    },
    addComment () {
      let fullComment = {}
      fullComment.id = this.comments.length
      fullComment.text = this.theComment
      this.comments.push(fullComment)
      this.theComment = ''
      this.playSound()
    }
  }
}
</script>

<style scoped>

</style>
