[merkle-patricia-tree](../README.md) › ["secure"](../modules/_secure_.md) › [SecureTrie](_secure_.securetrie.md)

# Class: SecureTrie

You can create a secure Trie where the keys are automatically hashed
using **keccak256** by using `import { SecureTrie as Trie } from 'merkle-patricia-tree'`.
It has the same methods and constructor as `Trie`.

**`class`** SecureTrie

**`extends`** Trie

## Hierarchy

  ↳ [CheckpointTrie](_checkpointtrie_.checkpointtrie.md)

  ↳ **SecureTrie**

## Index

### Constructors

* [constructor](_secure_.securetrie.md#constructor)

### Properties

* [EMPTY_TRIE_ROOT](_secure_.securetrie.md#empty_trie_root)
* [_checkpoints](_secure_.securetrie.md#_checkpoints)
* [_mainDB](_secure_.securetrie.md#_maindb)
* [_scratch](_secure_.securetrie.md#_scratch)
* [db](_secure_.securetrie.md#db)

### Accessors

* [isCheckpoint](_secure_.securetrie.md#ischeckpoint)
* [root](_secure_.securetrie.md#root)

### Methods

* [_createInitialNode](_secure_.securetrie.md#private-_createinitialnode)
* [_createScratchReadStream](_secure_.securetrie.md#private-_createscratchreadstream)
* [_deleteNode](_secure_.securetrie.md#private-_deletenode)
* [_enterCpMode](_secure_.securetrie.md#private-_entercpmode)
* [_exitCpMode](_secure_.securetrie.md#private-_exitcpmode)
* [_findDbNodes](_secure_.securetrie.md#private-_finddbnodes)
* [_findValueNodes](_secure_.securetrie.md#private-_findvaluenodes)
* [_formatNode](_secure_.securetrie.md#private-_formatnode)
* [_lookupNode](_secure_.securetrie.md#private-_lookupnode)
* [_saveStack](_secure_.securetrie.md#private-_savestack)
* [_setRoot](_secure_.securetrie.md#_setroot)
* [_updateNode](_secure_.securetrie.md#private-_updatenode)
* [_walkTrie](_secure_.securetrie.md#private-_walktrie)
* [batch](_secure_.securetrie.md#batch)
* [checkRoot](_secure_.securetrie.md#checkroot)
* [checkpoint](_secure_.securetrie.md#checkpoint)
* [commit](_secure_.securetrie.md#commit)
* [copy](_secure_.securetrie.md#copy)
* [createReadStream](_secure_.securetrie.md#createreadstream)
* [del](_secure_.securetrie.md#del)
* [findPath](_secure_.securetrie.md#findpath)
* [get](_secure_.securetrie.md#get)
* [put](_secure_.securetrie.md#put)
* [revert](_secure_.securetrie.md#revert)
* [createProof](_secure_.securetrie.md#static-createproof)
* [fromProof](_secure_.securetrie.md#static-fromproof)
* [prove](_secure_.securetrie.md#static-prove)
* [verifyProof](_secure_.securetrie.md#static-verifyproof)

## Constructors

###  constructor

\+ **new SecureTrie**(...`args`: any): *[SecureTrie](_secure_.securetrie.md)*

*Overrides [CheckpointTrie](_checkpointtrie_.checkpointtrie.md).[constructor](_checkpointtrie_.checkpointtrie.md#constructor)*

*Defined in [secure.ts:13](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/secure.ts#L13)*

**Parameters:**

Name | Type |
------ | ------ |
`...args` | any |

**Returns:** *[SecureTrie](_secure_.securetrie.md)*

## Properties

###  EMPTY_TRIE_ROOT

• **EMPTY_TRIE_ROOT**: *Buffer*

*Inherited from [Trie](_basetrie_.trie.md).[EMPTY_TRIE_ROOT](_basetrie_.trie.md#empty_trie_root)*

*Defined in [baseTrie.ts:45](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L45)*

The root for an empty trie

___

###  _checkpoints

• **_checkpoints**: *Buffer[]*

*Inherited from [CheckpointTrie](_checkpointtrie_.checkpointtrie.md).[_checkpoints](_checkpointtrie_.checkpointtrie.md#_checkpoints)*

*Defined in [checkpointTrie.ts:14](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/checkpointTrie.ts#L14)*

___

###  _mainDB

• **_mainDB**: *DB*

*Inherited from [CheckpointTrie](_checkpointtrie_.checkpointtrie.md).[_mainDB](_checkpointtrie_.checkpointtrie.md#_maindb)*

*Defined in [checkpointTrie.ts:12](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/checkpointTrie.ts#L12)*

___

###  _scratch

• **_scratch**: *ScratchDB | null*

*Inherited from [CheckpointTrie](_checkpointtrie_.checkpointtrie.md).[_scratch](_checkpointtrie_.checkpointtrie.md#_scratch)*

*Defined in [checkpointTrie.ts:13](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/checkpointTrie.ts#L13)*

___

###  db

• **db**: *DB*

*Inherited from [Trie](_basetrie_.trie.md).[db](_basetrie_.trie.md#db)*

*Defined in [baseTrie.ts:43](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L43)*

The backend DB

## Accessors

###  isCheckpoint

• **get isCheckpoint**(): *boolean*

*Inherited from [CheckpointTrie](_checkpointtrie_.checkpointtrie.md).[isCheckpoint](_checkpointtrie_.checkpointtrie.md#ischeckpoint)*

*Defined in [checkpointTrie.ts:29](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/checkpointTrie.ts#L29)*

Is the trie during a checkpoint phase?

**Returns:** *boolean*

___

###  root

• **get root**(): *Buffer*

*Inherited from [Trie](_basetrie_.trie.md).[root](_basetrie_.trie.md#root)*

*Defined in [baseTrie.ts:71](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L71)*

Gets the current root of the `trie`

**Returns:** *Buffer*

• **set root**(`value`: Buffer): *void*

*Inherited from [Trie](_basetrie_.trie.md).[root](_basetrie_.trie.md#root)*

*Defined in [baseTrie.ts:66](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L66)*

Sets the current root of the `trie`

**Parameters:**

Name | Type |
------ | ------ |
`value` | Buffer |

**Returns:** *void*

## Methods

### `Private` _createInitialNode

▸ **_createInitialNode**(`key`: Buffer, `value`: Buffer): *Promise‹void›*

*Inherited from [Trie](_basetrie_.trie.md).[_createInitialNode](_basetrie_.trie.md#private-_createinitialnode)*

*Defined in [baseTrie.ts:304](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L304)*

Creates the initial node from an empty tree.

**Parameters:**

Name | Type |
------ | ------ |
`key` | Buffer |
`value` | Buffer |

**Returns:** *Promise‹void›*

___

### `Private` _createScratchReadStream

▸ **_createScratchReadStream**(`scratchDb?`: ScratchDB): *ScratchReadStream‹›*

*Inherited from [CheckpointTrie](_checkpointtrie_.checkpointtrie.md).[_createScratchReadStream](_checkpointtrie_.checkpointtrie.md#private-_createscratchreadstream)*

*Defined in [checkpointTrie.ts:133](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/checkpointTrie.ts#L133)*

Returns a `ScratchReadStream` based on the state updates
since checkpoint.

**Parameters:**

Name | Type |
------ | ------ |
`scratchDb?` | ScratchDB |

**Returns:** *ScratchReadStream‹›*

___

### `Private` _deleteNode

▸ **_deleteNode**(`k`: Buffer, `stack`: TrieNode[]): *Promise‹void›*

*Inherited from [Trie](_basetrie_.trie.md).[_deleteNode](_basetrie_.trie.md#private-_deletenode)*

*Defined in [baseTrie.ts:439](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L439)*

Deletes a node from the database.

**Parameters:**

Name | Type |
------ | ------ |
`k` | Buffer |
`stack` | TrieNode[] |

**Returns:** *Promise‹void›*

___

### `Private` _enterCpMode

▸ **_enterCpMode**(): *void*

*Inherited from [CheckpointTrie](_checkpointtrie_.checkpointtrie.md).[_enterCpMode](_checkpointtrie_.checkpointtrie.md#private-_entercpmode)*

*Defined in [checkpointTrie.ts:103](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/checkpointTrie.ts#L103)*

Enter into checkpoint mode.

**Returns:** *void*

___

### `Private` _exitCpMode

▸ **_exitCpMode**(`commitState`: boolean): *Promise‹void›*

*Inherited from [CheckpointTrie](_checkpointtrie_.checkpointtrie.md).[_exitCpMode](_checkpointtrie_.checkpointtrie.md#private-_exitcpmode)*

*Defined in [checkpointTrie.ts:112](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/checkpointTrie.ts#L112)*

Exit from checkpoint mode.

**Parameters:**

Name | Type |
------ | ------ |
`commitState` | boolean |

**Returns:** *Promise‹void›*

___

### `Private` _findDbNodes

▸ **_findDbNodes**(`onFound`: FoundNodeFunction): *Promise‹void›*

*Inherited from [Trie](_basetrie_.trie.md).[_findDbNodes](_basetrie_.trie.md#private-_finddbnodes)*

*Defined in [baseTrie.ts:740](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L740)*

Finds all nodes that are stored directly in the db
(some nodes are stored raw inside other nodes)
called by {@link ScratchReadStream}

**Parameters:**

Name | Type |
------ | ------ |
`onFound` | FoundNodeFunction |

**Returns:** *Promise‹void›*

___

### `Private` _findValueNodes

▸ **_findValueNodes**(`onFound`: FoundNodeFunction): *Promise‹void›*

*Inherited from [Trie](_basetrie_.trie.md).[_findValueNodes](_basetrie_.trie.md#private-_findvaluenodes)*

*Defined in [baseTrie.ts:756](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L756)*

Finds all nodes that store k,v values
called by {@link TrieReadStream}

**Parameters:**

Name | Type |
------ | ------ |
`onFound` | FoundNodeFunction |

**Returns:** *Promise‹void›*

___

### `Private` _formatNode

▸ **_formatNode**(`node`: TrieNode, `topLevel`: boolean, `opStack`: BatchDBOp[], `remove`: boolean): *Buffer‹› | null | Buffer‹› | Buffer‹›[][]*

*Inherited from [CheckpointTrie](_checkpointtrie_.checkpointtrie.md).[_formatNode](_checkpointtrie_.checkpointtrie.md#private-_formatnode)*

*Overrides [Trie](_basetrie_.trie.md).[_formatNode](_basetrie_.trie.md#private-_formatnode)*

*Defined in [checkpointTrie.ts:152](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/checkpointTrie.ts#L152)*

Formats node to be saved by `levelup.batch`.

**Parameters:**

Name | Type | Default | Description |
------ | ------ | ------ | ------ |
`node` | TrieNode | - | the node to format. |
`topLevel` | boolean | - | if the node is at the top level. |
`opStack` | BatchDBOp[] | - | the opStack to push the node's data. |
`remove` | boolean | false | whether to remove the node (only used for CheckpointTrie). |

**Returns:** *Buffer‹› | null | Buffer‹› | Buffer‹›[][]*

The node's hash used as the key or the rawNode.

___

### `Private` _lookupNode

▸ **_lookupNode**(`node`: Buffer | Buffer[]): *Promise‹TrieNode | null›*

*Inherited from [Trie](_basetrie_.trie.md).[_lookupNode](_basetrie_.trie.md#private-_lookupnode)*

*Defined in [baseTrie.ts:314](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L314)*

Retrieves a node from db by hash.

**Parameters:**

Name | Type |
------ | ------ |
`node` | Buffer &#124; Buffer[] |

**Returns:** *Promise‹TrieNode | null›*

___

### `Private` _saveStack

▸ **_saveStack**(`key`: Nibbles, `stack`: TrieNode[], `opStack`: BatchDBOp[]): *Promise‹void›*

*Inherited from [Trie](_basetrie_.trie.md).[_saveStack](_basetrie_.trie.md#private-_savestack)*

*Defined in [baseTrie.ts:567](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L567)*

Saves a stack of nodes to the database.

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`key` | Nibbles | the key. Should follow the stack |
`stack` | TrieNode[] | a stack of nodes to the value given by the key |
`opStack` | BatchDBOp[] | a stack of levelup operations to commit at the end of this funciton  |

**Returns:** *Promise‹void›*

___

###  _setRoot

▸ **_setRoot**(`value?`: Buffer): *void*

*Inherited from [Trie](_basetrie_.trie.md).[_setRoot](_basetrie_.trie.md#_setroot)*

*Defined in [baseTrie.ts:75](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L75)*

**Parameters:**

Name | Type |
------ | ------ |
`value?` | Buffer |

**Returns:** *void*

___

### `Private` _updateNode

▸ **_updateNode**(`k`: Buffer, `value`: Buffer, `keyRemainder`: Nibbles, `stack`: TrieNode[]): *Promise‹void›*

*Inherited from [Trie](_basetrie_.trie.md).[_updateNode](_basetrie_.trie.md#private-_updatenode)*

*Defined in [baseTrie.ts:336](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L336)*

Updates a node.

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`k` | Buffer | - |
`value` | Buffer | - |
`keyRemainder` | Nibbles | - |
`stack` | TrieNode[] |   |

**Returns:** *Promise‹void›*

___

### `Private` _walkTrie

▸ **_walkTrie**(`root`: Buffer, `onFound`: FoundNodeFunction): *Promise‹void›*

*Inherited from [Trie](_basetrie_.trie.md).[_walkTrie](_basetrie_.trie.md#private-_walktrie)*

*Defined in [baseTrie.ts:208](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L208)*

Walks a trie until finished.

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`root` | Buffer | - |
`onFound` | FoundNodeFunction | callback to call when a node is found |

**Returns:** *Promise‹void›*

Resolves when finished walking trie.

___

###  batch

▸ **batch**(`ops`: BatchDBOp[]): *Promise‹void›*

*Inherited from [Trie](_basetrie_.trie.md).[batch](_basetrie_.trie.md#batch)*

*Defined in [baseTrie.ts:639](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L639)*

The given hash of operations (key additions or deletions) are executed on the DB

**`example`** 
const ops = [
   { type: 'del', key: Buffer.from('father') }
 , { type: 'put', key: Buffer.from('name'), value: Buffer.from('Yuri Irsenovich Kim') }
 , { type: 'put', key: Buffer.from('dob'), value: Buffer.from('16 February 1941') }
 , { type: 'put', key: Buffer.from('spouse'), value: Buffer.from('Kim Young-sook') }
 , { type: 'put', key: Buffer.from('occupation'), value: Buffer.from('Clown') }
]
await trie.batch(ops)

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`ops` | BatchDBOp[] |   |

**Returns:** *Promise‹void›*

___

###  checkRoot

▸ **checkRoot**(`root`: Buffer): *Promise‹boolean›*

*Inherited from [Trie](_basetrie_.trie.md).[checkRoot](_basetrie_.trie.md#checkroot)*

*Defined in [baseTrie.ts:86](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L86)*

Checks if a given root exists.

**Parameters:**

Name | Type |
------ | ------ |
`root` | Buffer |

**Returns:** *Promise‹boolean›*

___

###  checkpoint

▸ **checkpoint**(): *void*

*Inherited from [CheckpointTrie](_checkpointtrie_.checkpointtrie.md).[checkpoint](_checkpointtrie_.checkpointtrie.md#checkpoint)*

*Defined in [checkpointTrie.ts:38](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/checkpointTrie.ts#L38)*

Creates a checkpoint that can later be reverted to or committed.
After this is called, no changes to the trie will be permanently saved until `commit` is called.
To override the checkpointing mechanism use `_maindb.put` to write directly write to db.

**Returns:** *void*

___

###  commit

▸ **commit**(): *Promise‹void›*

*Inherited from [CheckpointTrie](_checkpointtrie_.checkpointtrie.md).[commit](_checkpointtrie_.checkpointtrie.md#commit)*

*Defined in [checkpointTrie.ts:53](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/checkpointTrie.ts#L53)*

Commits a checkpoint to disk, if current checkpoint is not nested.
If nested, only sets the parent checkpoint as current checkpoint.

**`throws`** If not during a checkpoint phase

**Returns:** *Promise‹void›*

___

###  copy

▸ **copy**(`includeCheckpoints`: boolean): *[SecureTrie](_secure_.securetrie.md)*

*Overrides [CheckpointTrie](_checkpointtrie_.checkpointtrie.md).[copy](_checkpointtrie_.checkpointtrie.md#copy)*

*Defined in [secure.ts:90](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/secure.ts#L90)*

Returns a copy of the underlying trie with the interface of SecureTrie.

**Parameters:**

Name | Type | Default | Description |
------ | ------ | ------ | ------ |
`includeCheckpoints` | boolean | true | If true and during a checkpoint, the copy will contain the checkpointing metadata and will use the same scratch as underlying db.  |

**Returns:** *[SecureTrie](_secure_.securetrie.md)*

___

###  createReadStream

▸ **createReadStream**(): *ReadStream*

*Inherited from [Trie](_basetrie_.trie.md).[createReadStream](_basetrie_.trie.md#createreadstream)*

*Defined in [baseTrie.ts:722](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L722)*

The `data` event is given an `Object` that has two properties; the `key` and the `value`. Both should be Buffers.

**Returns:** *ReadStream*

Returns a [stream](https://nodejs.org/dist/latest-v12.x/docs/api/stream.html#stream_class_stream_readable) of the contents of the `trie`

___

###  del

▸ **del**(`key`: Buffer): *Promise‹void›*

*Overrides [Trie](_basetrie_.trie.md).[del](_basetrie_.trie.md#del)*

*Defined in [secure.ts:48](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/secure.ts#L48)*

Deletes a value given a `key`.

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`key` | Buffer |   |

**Returns:** *Promise‹void›*

___

###  findPath

▸ **findPath**(`key`: Buffer): *Promise‹Path›*

*Inherited from [Trie](_basetrie_.trie.md).[findPath](_basetrie_.trie.md#findpath)*

*Defined in [baseTrie.ts:149](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L149)*

Tries to find a path to the node for the given key.
It returns a `stack` of nodes to the closest node.

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`key` | Buffer | the search key  |

**Returns:** *Promise‹Path›*

___

###  get

▸ **get**(`key`: Buffer): *Promise‹Buffer | null›*

*Overrides [Trie](_basetrie_.trie.md).[get](_basetrie_.trie.md#get)*

*Defined in [secure.ts:23](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/secure.ts#L23)*

Gets a value given a `key`

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`key` | Buffer | the key to search for |

**Returns:** *Promise‹Buffer | null›*

A Promise that resolves to `Buffer` if a value was found or `null` if no value was found.

___

###  put

▸ **put**(`key`: Buffer, `val`: Buffer): *Promise‹void›*

*Overrides [Trie](_basetrie_.trie.md).[put](_basetrie_.trie.md#put)*

*Defined in [secure.ts:35](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/secure.ts#L35)*

Stores a given `value` at the given `key`.
For a falsey value, use the original key to avoid double hashing the key.

**Parameters:**

Name | Type |
------ | ------ |
`key` | Buffer |
`val` | Buffer |

**Returns:** *Promise‹void›*

___

###  revert

▸ **revert**(): *Promise‹void›*

*Inherited from [CheckpointTrie](_checkpointtrie_.checkpointtrie.md).[revert](_checkpointtrie_.checkpointtrie.md#revert)*

*Defined in [checkpointTrie.ts:73](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/checkpointTrie.ts#L73)*

Reverts the trie to the state it was at when `checkpoint` was first called.
If during a nested checkpoint, sets root to most recent checkpoint, and sets
parent checkpoint as current.

**Returns:** *Promise‹void›*

___

### `Static` createProof

▸ **createProof**(`trie`: [SecureTrie](_secure_.securetrie.md), `key`: Buffer): *Promise‹[Proof](../modules/_basetrie_.md#proof)›*

*Overrides [Trie](_basetrie_.trie.md).[createProof](_basetrie_.trie.md#static-createproof)*

*Defined in [secure.ts:68](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/secure.ts#L68)*

Creates a proof that can be verified using [SecureTrie.verifyProof](_secure_.securetrie.md#static-verifyproof).

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`trie` | [SecureTrie](_secure_.securetrie.md) | - |
`key` | Buffer |   |

**Returns:** *Promise‹[Proof](../modules/_basetrie_.md#proof)›*

___

### `Static` fromProof

▸ **fromProof**(`proof`: [Proof](../modules/_basetrie_.md#proof), `trie?`: [Trie](_basetrie_.trie.md)): *Promise‹[Trie](_basetrie_.trie.md)›*

*Inherited from [Trie](_basetrie_.trie.md).[fromProof](_basetrie_.trie.md#static-fromproof)*

*Defined in [baseTrie.ts:657](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/baseTrie.ts#L657)*

Saves the nodes from a proof into the trie. If no trie is provided a new one wil be instantiated.

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`proof` | [Proof](../modules/_basetrie_.md#proof) | - |
`trie?` | [Trie](_basetrie_.trie.md) |   |

**Returns:** *Promise‹[Trie](_basetrie_.trie.md)›*

___

### `Static` prove

▸ **prove**(`trie`: [SecureTrie](_secure_.securetrie.md), `key`: Buffer): *Promise‹[Proof](../modules/_basetrie_.md#proof)›*

*Overrides [Trie](_basetrie_.trie.md).[prove](_basetrie_.trie.md#static-prove)*

*Defined in [secure.ts:59](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/secure.ts#L59)*

prove has been renamed to [SecureTrie.createProof](_secure_.securetrie.md#static-createproof).

**`deprecated`** 

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`trie` | [SecureTrie](_secure_.securetrie.md) | - |
`key` | Buffer |   |

**Returns:** *Promise‹[Proof](../modules/_basetrie_.md#proof)›*

___

### `Static` verifyProof

▸ **verifyProof**(`rootHash`: Buffer, `key`: Buffer, `proof`: [Proof](../modules/_basetrie_.md#proof)): *Promise‹Buffer | null›*

*Overrides [Trie](_basetrie_.trie.md).[verifyProof](_basetrie_.trie.md#static-verifyproof)*

*Defined in [secure.ts:81](https://github.com/ethereumjs/merkle-patricia-tree/blob/master/src/secure.ts#L81)*

Verifies a proof.

**`throws`** If proof is found to be invalid.

**Parameters:**

Name | Type |
------ | ------ |
`rootHash` | Buffer |
`key` | Buffer |
`proof` | [Proof](../modules/_basetrie_.md#proof) |

**Returns:** *Promise‹Buffer | null›*

The value from the key.
