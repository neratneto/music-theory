<template>
<div class="container">
  <div class="layout">
    <div stye="text-align: center">
      <img width="200px" src="https://pngimage.net/wp-content/uploads/2018/06/png-clave-de-sol-5.png">
    </div>

    <div style="padding: 10px">
      <span :class="note === tone ? 'note-selected' : 'notes'" v-for="note in [ 'C', 'D', 'E', 'F', 'G', 'A', 'B']" :key="note" @click="selectNote(note)"> {{ note }} </span>
    </div>

    <div>
      <button class="button-generate generate-major" @click="generateScaleMajor">Generate major scale</button>
      <button class="button-generate generate-minor" @click="generateScaleMinor">Generate minor scale</button>
    </div>

    <p class="result" v-for="scale in notesGoodLooking" :key="scale">{{ scale }}</p>
  </div>
</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: () => ({
    arrayScales: [],
    tone: 'G',
  }),
  computed: {
    notesGoodLooking() {
      const scalesGoodLooking = []
      for (let scale of this.arrayScales) {
        scalesGoodLooking.push(
          scale.join(' ')
        )
      }
      return scalesGoodLooking
    }
  },
  methods: {
    generateScaleMajor() {
      const scale = []
      const arrayNotes = ['C', 'C#', 'D', 'D#', 'E', 'F', 'F#', 'G', 'G#', 'A', 'A#', 'B', 'C', 'C#', 'D', 'D#', 'E', 'F', 'F#', 'G', 'G#', 'A', 'A#', 'B']
      scale.push(this.tone)
      const indexTone = arrayNotes.indexOf(this.tone)
      scale.push(arrayNotes[indexTone + 2])
      scale.push(arrayNotes[indexTone + 4])
      scale.push(arrayNotes[indexTone + 5])
      scale.push(arrayNotes[indexTone + 7])
      scale.push(arrayNotes[indexTone + 9])
      scale.push(arrayNotes[indexTone + 11])
      scale.push(arrayNotes[indexTone + 12])
      this.arrayScales.unshift(scale)
    },
    generateScaleMinor() {
      const scale = []
      const arrayNotes = ['C', 'Db', 'D', 'Eb', 'E', 'F', 'Gb', 'G', 'Ab', 'A', 'Bb', 'B', 'C', 'Db', 'D', 'Eb', 'E', 'F', 'Gb', 'G', 'Ab', 'A', 'Bb', 'B']
      scale.push(this.tone)
      const indexTone = arrayNotes.indexOf(this.tone)
      scale.push(arrayNotes[indexTone + 2])
      scale.push(arrayNotes[indexTone + 3])
      scale.push(arrayNotes[indexTone + 5])
      scale.push(arrayNotes[indexTone + 7])
      scale.push(arrayNotes[indexTone + 8])
      scale.push(arrayNotes[indexTone + 10])
      scale.push(arrayNotes[indexTone + 12])
      this.arrayScales.unshift(scale)
    },
    selectNote(note) {
      this.tone = note
    }
  }
}
</script>

<style scoped>
.container {
  padding: 10px;
  margin: 40px
}

.layout {

  border-radius: 20px;
  box-shadow: 1px 1px 5px black;
}

@media screen and (min-width: 700px) {
  .layout {
    padding: 2vw;
    margin: 4vh 8vw;

  }
}

@media screen and (max-width: 700px) {
  .layout {
    padding: 2vh 0;
  }
}

.input {
  padding: 5px;
}

.result {
  font-size: 30px;
}

.notes {
  font-size: 24px;
  color: gray;
  cursor: pointer;
}

.note-selected {
  font-size: 24px;
  color: blue;
  cursor: pointer;
}

.generate-minor {
  background-color: #9775fa;

}

.generate-major {
  background-color: #3bc9db;

}

.button-generate {
  padding: 16px;
  box-shadow: 2px 2px 5px gray;
  color: white;
  font-size: 16px;
  border-radius: 20px;
  margin: 4px;
  border: none;
}
</style>
