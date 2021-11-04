# Practical
Praga
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue"></script>
</head>
<body>
    <div id="app">
        <h1> {{ title }} </h1>
        <div class="message" v-if="message">
            <p> {{ message }} </p>
        </div>
        <!-- new-note -->
        <div class="new-note">
            <input v-model="note.title" type="text">
            <textarea v-model="note.descr"></textarea>
            <button @click="addNote">New Note</button>
        </div>
        <!-- note-list -->
        <div class="notes">
            <div class="note" v-for="(note, index) in notes" :key="index">
                <div class="note-header">
                    <p> {{ note.title }} </p>
                </div>
                <div class="note-body">
                    <p> {{ note.descr }} </p>
                    <span> {{ note.date }} </span>
                </div>
            </div>
        </div>
    </div>

    <script>
        var app = new Vue ({
            el: '#app',
            data: {
                title: 'Note App',
                message: null,
                note: {
                    title: '',
                    description: '',
                },
                notes: [
                {
                    title: 'First Note',
                    description: 'Description for first note',
                    date: new Date(Date.now()).toLocaleString(),
                },
                {
                    title: 'Second Note',
                    description: 'Description for Second note',
                    date: new Date(Date.now()).toLocaleString(),
                },
                {
                    title: 'Third Note',
                    description: 'Description for third note',
                    date: new Date(Date.now()).toLocaleString(),
                },
            ]
            },
            methods: {
                addNote () {
                    //console.log(this.note)
                    let {title, descr} = this.note
                    if (title ==='') {
                        this.message = 'title can`t be blank!'
                        return false
                    }
                    this.notes.push({ 
                        title,
                        descr,
                        date: new Date(Date.now()).toLocaleString(),
                    }),
                    this.message = null,
                    this.note.title = '',
                    this.note.descr = ''
                }
            }
        })
    </script>
</body>
</html>
