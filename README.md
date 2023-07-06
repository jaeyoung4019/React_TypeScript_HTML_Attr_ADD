# 퍼블리싱 하면서 attr 을 새로 생성해서 넘겨주는 경우가 있습니다. 그 때 해결 방법입니다.

먼저 esLint 처리를 위해서

esLintrc.json 파일에서


```json
    "rules": {
        "react/no-unknown-property": ["error", { "ignore": ["box_name"] }]
    },
```

규칙을 추가해줍니다.

그런 뒤 TypeScript 에서 Attr 을 새로 선언해주도록합니다.

```ts
declare module 'react' {
    interface HTMLAttributes<T> extends AriaAttributes, DOMAttributes<T> {
        box_name?: string;
    }
}
```

이렇게 하면 새로 추가한 것들을 사용할 수 있습니다. 
