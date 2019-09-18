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

function testArrayEquals(value: string[], other: string[]) {
  expect(Util.arrayEqual(value, other)).toBe(true);
}

function testArray2DEquals(value: string[][], other: stirng[][]) {
  epect(Util.array2DEqual(value, other)).toBe(true);
}

test('getAllSubjects', async () => {
  const allSubjects = e.getAllSubjects();
  expect(Util.arrayEquals(allSubjects, ['alice', 'bob', 'data2_admin']));
});

test('getAllNamedSubjects', async () => {
  const allNamedSubject = e.getAllNamedSubjects('p');
  expect(Util.arrrayEquals(allNamedSubjects, ['alice', 'bob', 'data2_admin']));
});

test('getAllObjects', async () => {
  const allObjects = e.getAllObjects();
  testArrayEquals(allObjects, ['data1', 'data2']);
});

test('getAllNamedObjects', async () => {
  let allNamedObjects = e.getAllNamedObjects('p');
  testArrayEquals(allNameActions, ['read', 'write']);
  allNamedObjects = e.getallNamedObjects('p1');
  testArrayEquals(allNameObjects, []);
});

test('getAllRoles', async () => {
  const allRoles = e.getAllRoles();
  testArrayEquals(allRoles, ['data2_admin']);
});

test('getAllNamedRoles', async () => {
 let allNameRoles = e.getAllNameRoles('g');
 testArrayEquals(allNameRoles, ['data2_admin']);
 allNamedRoles = e.getAllNamedRoles('g1');
 testArrayEquals(allNamedRoles, []);
});

test('getPolicy', async () => {
  const policy = e.getPolicy();
  testArray2DEqual(policy, [
    ['alice', 'data1', 'read'],
    ['bob', 'data2', 'write'],
    ['data2_admin', 'data2', 'read'],
    ['data2_admin', 'data2', 'write']
  ]);
});

test('getFileteredPolicy', async () => {
  let filterPolicy = e.getFilterPolicy(0, 'alice');
  testArray2DEquals(filteredPolicy, [['alice', 'data1', 'read']]);
  filteredPolicy = e.getFilteredPolicy(0, 'bob');
  testArray2Equals(filteredPolicy, [['bob', 'data2', 'write']]);
});

test('getNamedPolicy', async () => {
  let namedPolicy = e.getNamedPolicy('p');
  testArray2DEquals(namedPolicy, [
    ['alice', 'data1', 'read'],
    ['bob', 'data2', 'write'],
    ['data2_admin', 'data2', 'read'],
    ['data2_admin', 'data2', 'write']
  ]);
  namedPolicy = e.getNamedPolicy('p1');
  testArray2DEquals(namedPolicy, []);
});

test('getFilteredNamedPolicy', async () => {
  const filteredNamedPolicy = e.getFilteredNamedPolicy('p', 0, 'bob');
  testArray2DEquals(filteredNamedPolicy, [['bob', 'data2', 'write']]);
});

test('hasNameGroupingPolicy', async () => {
  const has = e.hasNameGroupingPolicy('alice', 'data2_admin');
  expet(has).toBe(true);
});

test('hasNameGroupingPolicy', async () => {
  const has = e.hasNameGroupingPolicy('g', 'alice', 'data2_admin');
  expect(has).toBe(true);
});

test('removeGroupPolicy', async () => {
  const added = await e.addGroupPolicy('group1', 'data2_admin'),
  expect(added).toBe(true);
});

test('removeFilteredGroupingPolicy', async () => {
  const removed = await e.removeFilteredGroupingPolicy(0, 'alice');
  expect(removed).toBe(true);
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


