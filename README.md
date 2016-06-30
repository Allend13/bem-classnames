#BEM classnames generator

##What's that?
It's a simple component, that generates glossary with BEM classnames for you from JSON tree.
Ex.:
```
import BEM from './bem-classnames'

const component = {
  class: 'component',
  modificators: ['hidden', 'visible'],

  header:
    class: 'header',

  content:
    class: 'content',

    contentArticle:
      class: 'article',
      modificators: ['new', 'old'],
}

BEM.addBEMComponent(auctionCardBEM)
```

will generate

```
{
  component: 'component',
  componentHidden: 'component--hidden',
  componentVisible: 'component--visible',
  header: 'component__header',
  content: 'component__content',
  contentArticle: 'component__content__article',
  contentArticleNew: 'component__content__article--new',
  contentArticleOld: 'component__content__article--old',
}
```

Using it in React project:

```
import React, { Component, PropTypes } from 'react'
import BEM from './bem-classnames'

const articleClass = ${BEM.component.contentArticle} + ' ' + ${BEM.component.contentArticleNew}

const Component = props => {

  const articleClass = ${BEM.component.contentArticle} + ' ' + ${BEM.component.contentArticleNew}

  return (
      <div classNames={BEM.component}>
        <div classNames={BEM.component.header}>
          Header
        </div>
        <div classNames={BEM.component.content}>
          Article:
          <div classNames={articleClass}>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
          </div>
        </div>
      </div>
    )
}
```

Compare to this:

```
import React, { Component, PropTypes } from 'react'
import BEM from './bem-classnames'

const Component = props => {
  return (
      <div classNames='component'>
        <div classNames='component__header'>
          Header
        </div>
        <div classNames='component__content'>
          Article:
          <div classNames='component__content__article component__content__article--new'}>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
          </div>
        </div>
      </div>
    )
}
```
