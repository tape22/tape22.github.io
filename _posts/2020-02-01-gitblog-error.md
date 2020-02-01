---
layout: post
title: "[Github_Jekyll] did not find expected key while parsing a block mapping at line 2 column 1 오류 해결" 
categories: error
tags: error
---

깃허브 블로그 초기 세팅을 끝내고 _posts 에서 마크다운 파일을 만들어서 포스팅을 하려고 했는데, 다음과 같은 오류가 뜨면서 제대로 글이 올라가지 않았다.

레퍼런스들을 찾아보니 YAML 에러에 대해서는 _config.yml 파일 설정과 관련된 문제라거나, space 문제 등 공백으로 인해 생긴 문제여서 그것을 해결하라는 내용들이 많았다. 하지만 두 가지 모두 해당사항이 없었어서 오랜 시간동안 삽질을 했다.

해결법은 굉장히 간단한데, 포스팅 할 때 맨 위에 설정을 해줄 때 title 설정 시 제목을 "" 안에 넣어줘야한다. 그 전에는 title : post title name 이런 식으로 설정했었는데, title : "포스팅 제목"으로 하니 오류가 해결되었다.

```
---
layout: post
title: "[Github_Jekyll] did not find expected key while parsing a block mapping at line 2 column 1 오류 해결" 
categories: error
tags: error
---
```

만약 config 파일이나 공백 문제를 해결했음에도 Error: YAML Exception reading /Users/jungmin/Desktop/tape22.github.io/_posts/2020-01-29-sourcetree-error.md: (<unknown>): did not find expected key while parsing a block mapping at line 2 column 1과 같은 오류가 뜬다면 이 방법을 시도해보길 바란다.