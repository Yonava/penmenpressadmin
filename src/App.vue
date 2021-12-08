<template>
    <div>
        <center>
            <h1>PenmenPressMobile Admin Site</h1>
    
            <h3>Title</h3>
            <input type="text" v-model="title" />
            <h3>Image URL</h3>
            <input type="text" v-model="image" />
            <h3>Image Caption</h3>
            <input type="text" v-model="imageCaption" />
            <h3>Category (only 1)</h3>
            <input type="text" v-model="category" />
            <h3>Author</h3>
            <input type="text" v-model="author" />
            <h3>Date (as it appears on main press site)</h3>
            <input type="text" v-model="date" />
            <h3>Content (remove paragraph spacing)</h3>
            <textarea v-model="content" cols="200" rows="50"></textarea>
            <br>
            <button @click="jsonFormatter()">Format</button>

            <h2>JSON Output</h2>
        </center>
        
        <pre>{{ output }}</pre>
        
        <br><br><br><br><br><br>
        
    </div>
</template>

<script>

export default {
    name: 'App',
    data: () => {
        return {
            output: '',
            title: '',
            image: '',
            imageCaption: '',
            category: '',
            author: '',
            date: '',
            content: '',
        }
    },
    methods: {
        jsonFormatter() {
            this.output = 
                `\t\t{
                "title":"${this.title}",
                "image":"${this.image}",
                "imageCaption":"${this.imageCaption}",
                "category":"${this.category.toUpperCase()}",
                "author":"${this.author}",
                "date":"${this.date}",
                "content":"${this.content.replace(/\n\n/g, " ~")}"
                }`
        }
    }
}
</script>

<style>
input {
    width: 70vw;
}
</style>
