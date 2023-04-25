This is a [Sanity]() documentation.

# Sanity CMS
Start a New sanity studio Project.
```bash
npm create sanity@latest
```

Require npm package
```bash
npm i next-sanity sanity-plugin-vercel-deploy
```

### Sanity Setup

1st ::::::: [`pages/api/preview.ts`]:
```bash
import { NextApiRequest, NextApiResponse } from "next"

export default function preview(req:NextApiRequest, res:NextApiResponse) {
    res.clearPreviewData()
    res.writeHead(307, {Location: '/'})
    res.end()
  }
```
*****

2nd ::::::: [`pages/api/exit-preview.ts`]:
```bash
import { NextApiRequest, NextApiResponse } from "next"

export default function exit(req:NextApiRequest, res:NextApiResponse) {
    res.clearPreviewData()
    res.writeHead(307, {Location: '/'})
    res.end()
  }
```
*****

3rd ::::::: [`environment/index.ts`]:
```bash
export const projectId = process.env.SANITY_PROJECTID
export const dataset = process.env.SANITY_DATASET
export const sanityapi = process.env.SANITY_API_VERSION

```

*****

4th ::::::: [`sanity.config.ts`]:
```bash
import {defineConfig} from 'sanity'
import {deskTool} from 'sanity/desk'
import {visionTool} from '@sanity/vision'
import {schemaTypes} from './schemas'
import { vercelDeployTool } from 'sanity-plugin-vercel-deploy'

import { dataset, projectId } from './app/environment'

export default defineConfig({
  
	basePath: '/studio',
  name: 'Quiz-Website',
  title: 'Quiz-studio',

  projectId: 'wenar5y7',
  dataset: 'production',

  plugins: [
    deskTool(), 
    visionTool(),
    vercelDeployTool()
  ],

  schema: {
    types: schemaTypes,
  },
})


```

*****

5th ::::::: [`sanity.cli.ts`]:
```bash
import {defineCliConfig} from 'sanity/cli'
import { dataset, projectId } from '@/app/environment'

export default defineCliConfig({
  api: {
    projectId: projectId,
    dataset: dataset
  },
})

```

*****

6th ::::::: [`lib/sanity.client.ts`]:
```bash
import {createClient} from 'next-sanity'
import { dataset, projectId, sanityapi } from '@/app/environment'


export const client = createClient({
  projectId: projectId ,
  dataset: dataset  ,
  apiVersion: sanityapi, 
  useCdn: true, 
})
```

*****


7th ::::::: [`/pages/studio/[[...index]].tsx`]:
```bash
import Head from 'next/head'
import {NextStudio} from 'next-sanity/studio'
import {NextStudioHead} from 'next-sanity/studio/head'

import config from '../../sanity.config'

export default function StudioPage() {
  return (
    <>
      <Head>
        <NextStudioHead />
      </Head>
      <NextStudio config={config} />
    </>
  )
}
```

*****

8th ::::::: [`app/studio/[[...index]]/loading.tsx`]:
```bash
'use client'

import config from '../../../sanity.config'
import {NextStudioLoading} from 'next-sanity/studio/loading'

export default function Loading() {
  return <NextStudioLoading config={config} />
}
```

*****

9th ::::::: [`app/studio/[[...index]]/page.tsx`]:
```bash
'use client'

import {NextStudio} from 'next-sanity/studio'

import config from '../../../sanity.config'

export default function StudioPage() {
  //  Supports the same props as `import {Studio} from 'sanity'`, `config` is required
  return <NextStudio config={config} />
}
```

*****

10th ::::::: [`app/studio/[[...index]]/head.tsx`]:
```bash
// Re-export `NextStudioHead` as default if you're happy with the default behavior
export {NextStudioHead as default} from 'next-sanity/studio/head'

// To customize it, use it as a children component:
import {NextStudioHead} from 'next-sanity/studio/head'

export default function CustomStudioHead() {
  return (
    <>
      <NextStudioHead favicons={false} />
      <link
        rel="icon"
        type="image/png"
        sizes="32x32"
        href="https://www.sanity.io/static/images/favicons/favicon-32x32.png"
      />
    </>
  )
}
```

*****

## schema


### Relational Database