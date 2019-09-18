### node-casbin
---
https://github.com/casbin/node-casbin

```ts
// test/managementAPI.test.tx
import { newEnForcer, Enforce, Util } from '../src';

let e = {} as Enforcer;

beforeEach(async () => {
  e = await newEnforcer('examples/rbac_model.conf', 'examples/rbac_policy.csv');
});



test('removeFilteredNamedGroupingPolicy', async () => {
  const removed = await e.removeFilteredNamedGroupingPolicy('g', 0, 'alice');
  expect(removed).toBe(true);
});
```

```
```

```
```


