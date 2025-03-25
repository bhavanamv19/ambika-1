<template>
  <div>
    <h2>Share Your Story</h2>
    <form @submit.prevent="submitPost">
      <textarea v-model="post" placeholder="Write your story..."></textarea>
      <button type="submit">Share</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      post: ''
    }
  },
  methods: {
    async submitPost() {

      // Submit post to server or database
      const response = await fetch('/posts', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({ content: this.post })
      });
      const data = await response.json();
      console.log(data);

    }
  }
}
</script>
