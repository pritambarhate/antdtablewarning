# Antd Table Ajax Example

This repo was created for this stackoverflow question: https://stackoverflow.com/questions/76591547/how-can-i-resolve-typescript-warning-for-antd-tables-onchange-handler-in-the-of/76592192#76592192

The solution to this is on the "solution" branch: https://github.com/pritambarhate/antdtablewarning/tree/solution

Taken from here: https://ant.design/components/table#components-table-demo-ajax

To demonstrate TypeScript Warning in VS Code:

In VS Code

```tsx
<Table
      columns={columns}
      rowKey={(record) => record.login.uuid}
      dataSource={data}
      pagination={tableParams.pagination}
      loading={loading}
      onChange={handleTableChange}
    />
```

`onChange` function gives following warning:

```
Type '(pagination: TablePaginationConfig, filters: Record<string, FilterValue>, sorter: SorterResult<DataType>) => void' is not assignable to type '(pagination: TablePaginationConfig, filters: Record<string, FilterValue | null>, sorter: SorterResult<DataType> | SorterResult<...>[], extra: TableCurrentDataSource<...>) => void'.
  Types of parameters 'filters' and 'filters' are incompatible.
    Type 'Record<string, FilterValue | null>' is not assignable to type 'Record<string, FilterValue>'.
      'string' index signatures are incompatible.
        Type 'FilterValue | null' is not assignable to type 'FilterValue'.
          Type 'null' is not assignable to type '(boolean | Key)[]'.ts(2322)
InternalTable.d.ts(21, 5): The expected type comes from property 'onChange' which is declared here on type 'IntrinsicAttributes & TableProps<DataType> & { children?: ReactNode; } & { ref?: Ref<HTMLDivElement> | undefined; }'
(property) TableProps<DataType>.onChange?: ((pagination: TablePaginationConfig, filters: Record<string, FilterValue | null>, sorter: SorterResult<DataType> | SorterResult<...>[], extra: TableCurrentDataSource<...>) => void) | undefined
```

```
$ ./node_modules/.bin/tsc --version
```

```
Version 4.9.5
```