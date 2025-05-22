# https://tailwindcss.com/docs/word-break

[Original link](https://tailwindcss.com/docs/word-break)

## Examples

### Normal

Use thebreak-normalutility to only add line breaks at normal word break points:

The longest word in any of the major English language dictionaries ispneumonoultramicroscopicsilicovolcanoconiosis,a word that refers to a lung disease contracted from the inhalation of very fine silica particles, specifically from a volcano; medically, it is the same as silicosis.

```
<p class="break-normal">The longest word in any of the major...</p>
```

### Break All

Use thebreak-allutility to add line breaks whenever necessary, without trying to preserve whole words:

The longest word in any of the major English language dictionaries ispneumonoultramicroscopicsilicovolcanoconiosis,a word that refers to a lung disease contracted from the inhalation of very fine silica particles, specifically from a volcano; medically, it is the same as silicosis.

```
<p class="break-all">The longest word in any of the major...</p>
```

### Break Keep

Use thebreak-keeputility to prevent line breaks from being applied to Chinese/Japanese/Korean (CJK) text:

抗衡不屈不挠 (kànghéng bùqū bùnáo) 这是一个长词，意思是不畏强暴，奋勇抗争，坚定不移，永不放弃。这个词通常用来描述那些在面对困难和挑战时坚持自己信念的人，他们克服一切困难，不屈不挠地追求自己的目标。无论遇到多大的挑战，他们都能够坚持到底，不放弃，最终获得胜利。

```
<p class="break-keep">抗衡不屈不挠...</p>
```

For non-CJK text thebreak-keeputility has the same behavior as thebreak-normalutility.

### Responsive design

Prefixaword-breakutilitywith a breakpoint variant likemd:to only apply the utility atmediumscreen sizes and above:

```
<p class="break-normal md:break-all ...">  Lorem ipsum dolor sit amet...</p>
```

Learn more about using variants in thevariants documentation.
