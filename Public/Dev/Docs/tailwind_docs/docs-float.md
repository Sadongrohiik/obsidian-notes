# https://tailwindcss.com/docs/float

[Original link](https://tailwindcss.com/docs/float)

## Examples

### Floating elements to the right

Use thefloat-rightutility to float an element to the right of its container:

Maybe we can live without libraries, people like you and me. Maybe. Sure, we're too old to change the world, but what about that kid, sitting down, opening a book, right now, in a branch at the local library and finding drawings of pee-pees and wee-wees on the Cat in the Hat and the Five Chinese Brothers? Doesn't HE deserve better? Look. If you think this is about overdue fines and missing books, you'd better think again. This is about that kid's right to read a book without getting his mind warped! Or: maybe that turns you on, Seinfeld; maybe that's how y'get your kicks. You and your good-time buddies.

```
<article>  <img class="float-right ..." src="/img/mountains.jpg" />  <p>Maybe we can live without libraries, people like you and me. ...</p></article>
```

### Floating elements to the left

Use thefloat-leftutility to float an element to the left of its container:

Maybe we can live without libraries, people like you and me. Maybe. Sure, we're too old to change the world, but what about that kid, sitting down, opening a book, right now, in a branch at the local library and finding drawings of pee-pees and wee-wees on the Cat in the Hat and the Five Chinese Brothers? Doesn't HE deserve better? Look. If you think this is about overdue fines and missing books, you'd better think again. This is about that kid's right to read a book without getting his mind warped! Or: maybe that turns you on, Seinfeld; maybe that's how y'get your kicks. You and your good-time buddies.

```
<article>  <img class="float-left ..." src="/img/mountains.jpg" />  <p>Maybe we can live without libraries, people like you and me. ...</p></article>
```

### Using logical properties

Use thefloat-startandfloat-endutilities, which uselogical propertiesto map to either the left or right side based on the text direction:

left-to-right

Maybe we can live without libraries, people like you and me. Maybe. Sure, we're too old to change the world, but what about that kid, sitting down, opening a book, right now, in a branch at the local library and finding drawings of pee-pees and wee-wees on the Cat in the Hat and the Five Chinese Brothers? Doesn't HE deserve better? Look. If you think this is about overdue fines and missing books, you'd better think again. This is about that kid's right to read a book without getting his mind warped! Or: maybe that turns you on, Seinfeld; maybe that's how y'get your kicks. You and your good-time buddies.

right-to-left

ربما يمكننا العيش بدون مكتبات، أشخاص مثلي ومثلك. ربما. بالتأكيد، نحن أكبر من أن نغير العالم، ولكن ماذا عن ذلك الطفل الذي يجلس ويفتح كتابًا الآن في أحد فروع المكتبة المحلية ويجد رسومات للتبول والبول على القطة في القبعة والإخوة الصينيون الخمسة؟ ألا يستحق الأفضل؟ ينظر. إذا كنت تعتقد أن الأمر يتعلق بالغرامات المتأخرة والكتب المفقودة، فمن الأفضل أن تفكر مرة أخرى. يتعلق الأمر بحق ذلك الطفل في قراءة كتاب دون أن يتشوه عقله! أو: ربما يثيرك هذا يا سينفيلد؛ ربما هذه هي الطريقة التي تحصل بها على ركلاتك. أنت ورفاقك الطيبين.

```
<article>  <img class="float-start ..." src="/img/mountains.jpg" />  <p>Maybe we can live without libraries, people like you and me. ...</p></article><article dir="rtl">  <img class="float-start ..." src="/img/mountains.jpg" />  <p>... ربما يمكننا العيش بدون مكتبات، أشخاص مثلي ومثلك. ربما. بالتأكيد</p></article>
```

### Disabling a float

Use thefloat-noneutility to reset any floats that are applied to an element:

Maybe we can live without libraries, people like you and me. Maybe. Sure, we're too old to change the world, but what about that kid, sitting down, opening a book, right now, in a branch at the local library and finding drawings of pee-pees and wee-wees on the Cat in the Hat and the Five Chinese Brothers? Doesn't HE deserve better? Look. If you think this is about overdue fines and missing books, you'd better think again. This is about that kid's right to read a book without getting his mind warped! Or: maybe that turns you on, Seinfeld; maybe that's how y'get your kicks. You and your good-time buddies.

```
<article>  <img class="float-none ..." src="/img/mountains.jpg" />  <p>Maybe we can live without libraries, people like you and me. ...</p></article>
```

### Responsive design

Prefixafloatutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<img class="float-right md:float-left" src="/img/mountains.jpg" />
```

Learn more about using variants in thevariants documentation.
