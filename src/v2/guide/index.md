---
title: הקדמה
type: guide
order: 2
---

## מה זה Vue.js?

Vue (מבוטא ויו, כמו **view**) הוא **פריימוורק פרוגרסיבי** לבניית ממשקי משתמש. שלא כמו מסגרות מונוליטיות אחרות, Vue מתוכנן מהיסוד כך שניתן יהיה לאמץ אותו באופן הדרגתי. ליבת הספרייה ממוקדת בשכבת התצוגה בלבד, והיא קלה לשילוב עם ספריות אחרות או פרויקטים קיימים. מצד שני, Vue גם מסוגל להפעיל Single-Page Applications מתוחכמים כאשר משתמשים בהם בשילוב עם [כלים מודרניים](single-file-components.html) ו[ספריות עזר](https://github.com/vuejs/awesome-vue#components--libraries).

אם תרצה ללמוד עוד על Vue לפני שאתה צולל פנימה, <a id="modal-player"  href="#">יצרנו סרטון</a> שעובר על עקרונות הליבה ופרויקט לדוגמא.

אם אתה מפתח פרונט-אנד מנוסה ורוצה לדעת איך Vue משתווה לספריות/מסגרות אחרות, בדוק את [ההשוואה עם מסגרות אחרות](comparison.html).

<div class="vue-mastery"><a href="https://www.vuemastery.com/courses/intro-to-vue-js/vue-instance/" target="_blank" rel="sponsored noopener" title="Free Vue.js Course">צפה בקורס וידאו בחינם ב-Vue Mastery</a></div>

## מתחילים

<a class="button" href="installation.html">התקנה</a>

<p class="tip">המדריך הרשמי מניח שיש לך ידע ברמה בינונית ב- HTML, CSS ו- JavaScript. אם אתה חדש לחלוטין בפיתוח פרונט-אנד, יתכן שזה לא יהיה הרעיון הטוב ביותר לקפוץ ישר לפריימוורק כצעד הראשון שלך - למד את היסודות ואז חזור! ניסיון קודם עם מסגרות אחרות עוזר, אך אינו נדרש.</p>

הדרך הקלה ביותר לנסות את Vue.js היא באמצעות הדוגמה [Hello World example](https://codesandbox.io/s/github/vuejs/vuejs.org/tree/master/src/v2/examples/vue-20-hello-world). אל תהסס לפתוח אותו בלשונית אחרת ולעקוב אחריה כשאנחנו עוברים על כמה דוגמאות בסיסיות. לחלופין, אתה יכול <a href="https://github.com/vuejs/vuejs.org/blob/master/src/v2/examples/vue-20-hello-world/index.html" target="_blank" download="index.html" rel="noopener noreferrer">ליצור קובץ <code>index.html</code></a> ולכלול Vue עם:

```html
<!-- development version, includes helpful console warnings -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

או:

```html
<!-- production version, optimized for size and speed -->
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```

דף ה[התקנה](installation.html) מציעה יותר אפשרויות להתקנת Vue. הערה: אנחנו **לא** מציעים למתחילים להתחיל עם `vue-cli`, במיוחד אם אינך מכיר עדיין כלי בנייה מבוססי Node.js.

אם אתה מעדיף משהו אינטראקטיבי יותר, אתה יכול גם לבדוק את [סדרת ההדרכה הזו של Scrimba](https://scrimba.com/g/gvuedocs), שנותנת לך שילוב של screencasts ו-code playground שאתה יכול להשהות ולשחק איתם בכל עת.

## רינדור הצהרתי

<div class="scrimba"><a href="https://scrimba.com/p/pXKqta/cQ3QVcr" target="_blank" rel="noopener noreferrer">נסה את השיעור הזה ב-Scrimba</a></div>

בליבה של Vue.js נמצאת מערכת המאפשרת לנו לרנדר אלמנטים ל-DOM באופן הצהרתי באמצעות תחביר פשוט:

```html
<div id="app">
  {{ message }}
</div>
```

```js
var app = new Vue({
  el: "#app",
  data: {
    message: "שלום Vue!"
  }
});
```

{% raw %}

<div id="app" class="demo">
  {{ message }}
</div>
<script>
var app = new Vue({
  el: '#app',
  data: {
    message: 'שלום Vue!'
  }
})
</script>
{% endraw %}

יצרנו כבר את אפליקציית ה- Vue הראשונה שלנו! זה נראה די דומה לביצוע string template, אך Vue עשתה הרבה עבודה מתחת למכסה המנוע. הנתונים (data) וה-DOM מקושרים כעת, ועכשיו הכל **תגובתי**. איך אנחנו יודעים? פתח את קונסולת ה- JavaScript של הדפדפן שלך (עכשיו, בדף זה) והגדר את `app.message` לערך אחר. אתה אמור לראות את הדוגמה שניתנה לעיל מתעדכנת בהתאם.

בנוסף לאינטרפולציה של טקסט, בצורה כזאת אנו יכולים לחבר attributes של אלמנטים:

```html
<div id="app-2">
  <span v-bind:title="message">
    רחף עם העכבר מעלי למשך כמה שניות כדי לראות את ה title שלי המחוברת באופן
    דינמי!
  </span>
</div>
```

```js
var app2 = new Vue({
  el: "#app-2",
  data: {
    message: "דף זה נטען ב " + new Date().toLocaleString()
  }
});
```

{% raw %}

<div id="app-2" class="demo">
  <span v-bind:title="message">
    רחף עם העכבר מעלי למשך כמה שניות כדי לראות את ה-title שלי המחוברת באופן
    דינמי!
  </span>
</div>
<script>
var app2 = new Vue({
  el: '#app-2',
  data: {
    message: 'דף זה נטען ב ' + new Date().toLocaleString()
  }
})
</script>
{% endraw %}

כאן אנו נתקלים במשהו חדש. ה-`v-bind`attribute שאתה רואה נקרא Directives .**directive**, נפתחות עם `v-` כדי לציין שמדובר בתכונות מיוחדות המסופקות על ידי Vue, וכפי שאפשר לנחש, הם מיישמים התנהגות תגובתית מיוחדת על ה-DOM המוצג. כאן זה בעצם אומר “שמור על ה-`title`attribute שיהיה מעודכנת עם המאפיין (property) `message`של ה-Vue instance”.

אם תפתח שוב את קונסולת ה- JavaScript שלך ותכניס `app2.message = 'איזה הודעה חדשה'`, תראה שוב כי ה-HTML המחובר - במקרה זה ה`title` attribute- עודכן.

## תנאים ולולאות

<div class="scrimba"><a href="https://scrimba.com/p/pXKqta/cEQe4SJ" target="_blank" rel="noopener noreferrer">נסה את השיעור הזה ב-Scrimba</a></div>

קל לשלוט על נוכחות של אלמנט:

```html
<div id="app-3">
  <span v-if="seen">עכשיו אתה רואה אותי</span>
</div>
```

```js
var app3 = new Vue({
  el: "#app-3",
  data: {
    seen: true
  }
});
```

{% raw %}

<div id="app-3" class="demo">
  <span v-if="seen">עכשיו אתה רואה אותי</span>
</div>
<script>
var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
</script>
{% endraw %}

נסה להכניס `app3.seen = false` בתוך הקונסול. ההודעה אמורה להיעלם.

דוגמה זו ממחישה שאנחנו יכולים לחבר נתונים לא רק לטקסט ו-attributes, אלא גם את ה**מבנה** של ה-DOM. יתר על כן, Vue מספקת גם מערכת אפקט מעבר (transition effect) חזקה שיכולה להחיל אוטומטית [אפקטי מעבר](transitions.html) כאשר אלמנטים מוכנסים / מעודכנים / מוסרים על ידי Vue.

ישנן לא מעט directives אחרות, לכל אחת פונקציונליות מיוחדת משלה. לדוגמה, ניתן להשתמש עם ה-`v-for` directive להצגת רשימת פריטים המשתמשים בנתונים מתוך מערך:

```html
<div id="app-4">
  <ol>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
</div>
```

```js
var app4 = new Vue({
  el: "#app-4",
  data: {
    todos: [
      { text: "למד ג'אווה סקריפט" },
      { text: "למד Vue" },
      { text: "בנה משהו מדהים" }
    ]
  }
});
```

{% raw %}

<div id="app-4" class="demo">
  <ol>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
</div>
<script>
var app4 = new Vue({
  el: '#app-4',
  data: {
    todos: [
      { text: "למד ג'אווה סקריפט" },
      { text: "למד Vue" },
      { text: "בנה משהו מדהים" }
    ]
  }
})
</script>
{% endraw %}

בתוך הקונסול, הכנס `app4.todos.push({ text: 'פריט חדש' })`. אתה אמור לראות פריט חדש שמצורף לרשימה.

## טיפול בקלט משתמשים

<div class="scrimba"><a href="https://scrimba.com/p/pXKqta/czPNaUr" target="_blank" rel="noopener noreferrer">נסה את השיעור הזה ב-Scrimba</a></div>

כדי לאפשר למשתמשים ליצור אינטראקציה עם האפליקציה שלך, אנו יכולים להשתמש עם ה directive `v-on` כדי לצרף מאזינים לאירועים המפעילים מתודות ב-Vue instance שלנו:

```html
<div id="app-5">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">הפוך את ההודעה</button>
</div>
```

```js
var app5 = new Vue({
  el: "#app-5",
  data: {
    message: "שלום Vue.js!"
  },
  methods: {
    reverseMessage: function() {
      this.message = this.message
        .split("")
        .reverse()
        .join("");
    }
  }
});
```

{% raw %}

<div id="app-5" class="demo">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">הפוך את ההודעה</button>
</div>
<script>
var app5 = new Vue({
  el: '#app-5',
  data: {
    message: 'שלום Vue.js!'
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
})
</script>
{% endraw %}

שימו לב שבשיטה זו אנו מעדכנים את ה-state (מצב) של האפליקציה שלנו בלי לגעת ב-DOM - כל המניפולציות של ה-DOM מנוהלות על ידי Vue, והקוד שאתם כותבים מתמקד בלוגיקה שבבסיס.

Vue מספקת גם את ה-`v-model` directive שהופכת את הכריכה הדו-כיוונית בין קלט הטופס ל-state של האפליקציה לקלה ביותר:

```html
<div id="app-6">
  <p>{{ message }}</p>
  <input v-model="message" />
</div>
```

```js
var app6 = new Vue({
  el: "#app-6",
  data: {
    message: "שלום Vue!"
  }
});
```

{% raw %}

<div id="app-6" class="demo">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
<script>
var app6 = new Vue({
  el: '#app-6',
  data: {
    message: 'שלום Vue!'
  }
})
</script>
{% endraw %}

## יצירה של קומפוננטות

<div class="scrimba"><a href="https://scrimba.com/p/pXKqta/cEQVkA3" target="_blank" rel="noopener noreferrer">נסה את השיעור הזה ב-Scrimba</a></div>

מערכת הקומפוננטות היא מושג חשוב נוסף ב- Vue, מכיוון שהיא הפשטה המאפשרת לנו לבנות אפליקציות בקנה מידה גדול המורכב מרכיבים קטנים, עצמאים ולעתים קרובות - לשימוש חוזר. אם אנו חושבים על זה, כמעט כל סוג של ממשק אפליקציה יכול להיות מופשט לעץ של קומפונטות:

![Component Tree](/images/components.png)

ב-Vue, קומפוננטה הוא למעשה instance Vue עם אפשרויות מוגדרות מראש. רישום קומפוננטה הוא מאוד פשוט:

```js
// Define a new component called todo-item
Vue.component('todo-item', {
  template: '<li>זה משימה</li>'
})

var app = new Vue(...)
```

עכשיו אתה יכול לצרף את זה ל-instance של קומפוננטה אחרת:

```html
<ol>
  <!-- Create an instance of the todo-item component -->
  <todo-item></todo-item>
</ol>
```

הבעיה הוא  שזה יתן את אותו טקסט לכל משימה, שאינו מעניין במיוחד. עלינו להיות מסוגלים להעביר נתונים מהקומפוננטה ההורה לקומפוננטות הילדים. אז בואו לשנות את הגדרת הקומפוננטה בכדי לגרום לו לקבל [prop](components.html#Props):

```js
Vue.component("todo-item", {
  // The todo-item component now accepts a
  // "prop", which is like a custom attribute.
  // This prop is called todo.
  props: ["todo"],
  template: "<li>{{ todo.text }}</li>"
});
```

כעת נוכל להעביר את המשימה (todo) לכל קומפוננטה חוזר באמצעות `v-bind`:

```html
<div id="app-7">
  <ol>
    <!--
      Now we provide each todo-item with the todo object
      it's representing, so that its content can be dynamic.
      We also need to provide each component with a "key",
      which will be explained later.
    -->
    <todo-item
      v-for="item in groceryList"
      v-bind:todo="item"
      v-bind:key="item.id"
    ></todo-item>
  </ol>
</div>
```

```js
Vue.component("todo-item", {
  props: ["todo"],
  template: "<li>{{ todo.text }}</li>"
});

var app7 = new Vue({
  el: "#app-7",
  data: {
    groceryList: [
      { id: 0, text: "ירקות" },
      { id: 1, text: "גבינה" },
      { id: 2, text: "כל משהו אחר שבן אדם אמור לאכול" }
    ]
  }
});
```

{% raw %}

<div id="app-7" class="demo">
  <ol>
    <todo-item v-for="item in groceryList" v-bind:todo="item" :key="item.id"></todo-item>
  </ol>
</div>
<script>
Vue.component('todo-item', {
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})
var app7 = new Vue({
  el: '#app-7',
  data: {
    groceryList: [
      { id: 0, text: "ירקות" },
      { id: 1, text: "גבינה" },
      { id: 2, text: "כל משהו אחר שבן אדם אמור לאכול" }
    ]
  }
})
</script>
{% endraw %}

זאת דוגמא מבוימת, אך למעשה הצלחנו להפריד את האפליקציה שלנו לשתי יחידות קטנות יותר, והילד מנותק היטב מההורה דרך ממשק ה-props. כעת אנו יכולים לשפר עוד יותר את `<todo-item>` קומפוננטה שלנו עם תבנית והגיון מורכבים יותר מבלי להשפיע על קומפוננטת האב (ה-app).

באפליקציה גדולה, יש צורך לחלק את האפליקציה כולה לקומפוננטות כדי לאפשר לנהל את הפיתוח בצורה מיטבית. נדבר הרבה יותר על קומפוננטות [בהמשך המדריך](component.html), אך הנה דוגמה (דמיונית) לאופן שבו תבנית של אפליקציה עשויה להיראות עם קומפוננטות:

```html
<div id="app">
  <app-nav></app-nav>
  <app-view>
    <app-sidebar></app-sidebar>
    <app-content></app-content>
  </app-view>
</div>
```

### היחס ל-Custom Elements

אולי שמתם לב שמרכיבי Vue דומים מאוד ל- ** Custom Elements **, שהם חלק מ [Spec Components Web](https://www.w3.org/wiki/WebComponents/). הסיבה לכך היא שתחביר הרכיבים של Vue מעוצב בצורה רופפת לפי המפרט. לדוגמה, קומפוננטי Vue מיישמים את [Slot API](https://github.com/w3c/webcomponents/blob/gh-pages/proposals/Slots-Proposal.md)-ואת  ה`is` atrribute המיוחדת. עם זאת, ישנם כמה הבדלים עיקריים:

1. מפרט ה-Web Components Spec הושלם סופית, אך אינו מיושם באופן מקומי בכל דפדפן. ספארי 10.1+, Chrome 54+ ו- Firefox 63+ תומכים באופן טבעי ב-Web Components. לשם השוואה, קומפוננטות Vue אינם דורשים polyfills ופועלים בעקביות בכל הדפדפנים הנתמכים (IE9 ומעלה). במידת הצורך, ניתן לעטוף קומפוננטות Vue בתוך custom element.

2. קומפוננטות Vue מספקות תכונות חשובות שאינן זמינות ב-custom elements רגילים, ובמיוחד זרימת נתונים חוצה קומפוננטות, תקשורת אירועים בהתאמה אישית ושילובי כלים לבנייה.

למרות ש- Vue אינו משתמש custom elements באופן פנימי, יש לו [יכולת פעולה הדדית רבה](https://custom-elements-everywhere.com/#vue) בכל מה שקשור לצריכה או הפצה כ-custom elements. Vue CLI תומך גם בבניית קומפוננטות Vue שרושמים את עצמם כ-custom elements מקוריים.

## מוכן לעוד?

הצגנו בקצרה את התכונות הבסיסיות ביותר של ליבת Vue.js - שאר מדריך זה יכסה אותם ותכונות מתקדמות אחרות עם פרטים עדינים בהרבה, אז הקפידו לקרוא את הכל!

<div id="video-modal" class="modal"><div class="video-space" style="padding: 56.25% 0 0 0; position: relative;"><iframe src="https://player.vimeo.com/video/247494684?dnt=1" style="height: 100%; left: 0; position: absolute; top: 0; width: 100%; margin: 0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe></div><script src="https://player.vimeo.com/api/player.js"></script><p class="modal-text">Video by <a href="https://www.vuemastery.com" target="_blank" rel="sponsored noopener" title="Vue.js Courses on Vue Mastery">Vue Mastery</a>. Watch Vue Mastery’s free <a href="https://www.vuemastery.com/courses/intro-to-vue-js/vue-instance/" target="_blank" rel="sponsored noopener" title="Vue.js Courses on Vue Mastery">Intro to Vue course</a>.</div>
