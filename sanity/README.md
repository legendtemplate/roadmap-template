This is a [Sanity]() documentation.
This is a [Sanity]() youtube channel.

# Sanity CMS

Start a New sanity studio Project.

```bash
npm create sanity@latest
```

## schemas

```bash
import {defineField, defineType} from 'sanity'
```

---

```bash
export default defineType({
  name: 'post',
  title: 'Post',
  type: 'document',
    fields: []
)}
```

---

```bash
import author from './author'
export const schemaTypes = [author]
```

groq`*[_type == "author"]{_id,_createdAt}`
---

### string

```bash
  defineField({
      name: 'name',
      title: 'Name',
      type: 'string',
      description: 'Make it catchy',
    }),

```
> name
---

### text

```bash
 defineField({
  title: 'Description',
  name: 'description',
  type: 'text'
})
```
> description
---

### image

```bash
 defineField({
      name: 'image',
      title: 'Image',
      type: 'image',
      options: {
        hotspot: true,
      },
        fields: [
          {
      name: 'caption',
      type: 'string',
      title: 'Caption',
    },
    {
      name: 'attribution',
      type: 'string',
      title: 'Attribution',
    }
        ]
    }),
```
> "image": image.asset->url,
> "imageAtt": image.attribution,
> "imageCap": image.caption,
---

### slug

```bash
 defineField({
  title: 'Slug',
  name: 'slug',
  type: 'slug',
  options: {
    source: 'title',
    maxLength: 96,
  }
})
```
> "slug": slug.current,
---

### date

```bash
{
  title: 'Release date',
  name: 'releaseDate',
  type: 'date',
  options: {
    dateFormat: 'YYYY-MM-DD',
    calendarTodayLabel: 'Today'
  }
}
```

---

### datetime

```bash
{
  title: 'Launch Scheduled At',
  name: 'launchAt',
  type: 'datetime',
  options: {
    dateFormat: 'YYYY-MM-DD',
    timeFormat: 'HH:mm',
    timeStep: 15,
    calendarTodayLabel: 'Today'
  }
}
```

---

### preview

```bash
   preview: {
    select: {
      title: 'name',
      media: 'image',
    },
  },
```