<script>
export default {
  name: "FetchJson",
  props: {
    url: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      json: []
    }
  },
  created() {
    console.log(this.url)
    fetch(this.url, {
      headers: {
        "Content-Type": "application/json",
        Accept: "application/json"
      }
    })
      .then(response => {
        console.log(response.body)
        return response.json()
      })
      .then(json => {
        this.json = json.results
        console.log(this.json)
      })
      .catch(e => console.log(e))
  },
  render() {
    return this.$scopedSlots.default({
      json: this.json
    })
  }
}
</script>
