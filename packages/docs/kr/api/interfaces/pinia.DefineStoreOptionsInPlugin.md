---
sidebar: "auto"
editLinks: false
sidebarDepth: 3
---

[API Documentation](../index.md) / [pinia](../modules/pinia.md) / DefineStoreOptionsInPlugin

# Interface: DefineStoreOptionsInPlugin<Id, S, G, A\>

[pinia](../modules/pinia.md).DefineStoreOptionsInPlugin

Available `options` when creating a pinia plugin.

## Type parameters

| Name | Type |
| :------ | :------ |
| `Id` | extends `string` |
| `S` | extends [`StateTree`](../modules/pinia.md#statetree) |
| `G` | `G` |
| `A` | `A` |

## Hierarchy

- `Omit`<[`DefineStoreOptions`](pinia.DefineStoreOptions.md)<`Id`, `S`, `G`, `A`\>, ``"id"`` \| ``"actions"``\>

  ↳ **`DefineStoreOptionsInPlugin`**

## Properties

### actions

• **actions**: `A`

Extracted object of actions. Added by useStore() when the store is built
using the setup API, otherwise uses the one passed to `defineStore()`.
Defaults to an empty object if no actions are defined.

#### Defined in

[packages/pinia/src/types.ts:721](https://github.com/vuejs/pinia/blob/2b998ee/packages/pinia/src/types.ts#L721)

___

### getters

• `Optional` **getters**: `G` & `ThisType`<`UnwrapRef`<`S`\> & [`_StoreWithGetters`](../modules/pinia.md#_storewithgetters)<`G`\> & [`PiniaCustomProperties`](pinia.PiniaCustomProperties.md)<`string`, [`StateTree`](../modules/pinia.md#statetree), [`_GettersTree`](../modules/pinia.md#_getterstree)<[`StateTree`](../modules/pinia.md#statetree)\>, [`_ActionsTree`](../modules/pinia.md#_actionstree)\>\> & [`_GettersTree`](../modules/pinia.md#_getterstree)<`S`\>

Optional object of getters.

#### Inherited from

Omit.getters

#### Defined in

[packages/pinia/src/types.ts:645](https://github.com/vuejs/pinia/blob/2b998ee/packages/pinia/src/types.ts#L645)

## Methods

### hydrate

▸ `Optional` **hydrate**(`storeState`, `initialState`): `void`

Allows hydrating the store during SSR when complex state (like client side only refs) are used in the store
definition and copying the value from `pinia.state` isn't enough.

**`example`**
If in your `state`, you use any `customRef`s, any `computed`s, or any `ref`s that have a different value on
Server and Client, you need to manually hydrate them. e.g., a custom ref that is stored in the local
storage:

```ts
const useStore = defineStore('main', {
  state: () => ({
    n: useLocalStorage('key', 0)
  }),
  hydrate(storeState, initialState) {
    // @ts-expect-error: https://github.com/microsoft/TypeScript/issues/43826
    storeState.n = useLocalStorage('key', 0)
  }
})
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `storeState` | `UnwrapRef`<`S`\> | the current state in the store |
| `initialState` | `UnwrapRef`<`S`\> | initialState |

#### Returns

`void`

#### Inherited from

Omit.hydrate

#### Defined in

[packages/pinia/src/types.ts:685](https://github.com/vuejs/pinia/blob/2b998ee/packages/pinia/src/types.ts#L685)

___

### state

▸ `Optional` **state**(): `S`

Function to create a fresh state. **Must be an arrow function** to ensure
correct typings!

#### Returns

`S`

#### Inherited from

Omit.state

#### Defined in

[packages/pinia/src/types.ts:640](https://github.com/vuejs/pinia/blob/2b998ee/packages/pinia/src/types.ts#L640)
