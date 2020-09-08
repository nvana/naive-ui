# Duration
Auto close.
```html
<n-button @click="notify('info')">
  Duration: 10000
</n-button>
```
```js
export default {
  methods: {
    notify (type) {
      let count = 10
      const notification = this.$NNotification.open({
        title: `What is Pingshan Road + rain ?`,
        content: `You have ${count} seconds to answer the question.`,
        duration: 10000,
        closable: false,
        onAfterShow: () => {
          const minusCount = () => {
            count--
            notification.content = `You have ${count} seconds to answer the question.`
            if (count > 0) {
              window.setTimeout(minusCount, 1000)
            }
          }
          window.setTimeout(minusCount, 1000)
        },
        onAfterHide: () => {
          this.$NNotification.open({
            title: `The Answer is Pingshan River!`,
            content: 'Oops, that is not even an anti-humor.',
            duration: 10000
          })
        }
      })
    }
  }
}
```
```css
.n-button {
  margin: 0 12px 8px 0;
}
```