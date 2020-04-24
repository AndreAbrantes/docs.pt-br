---
title: Metadados
ms.date: 12/13/2019
description: Saiba como recuperar metadados sobre o banco de dados.
ms.openlocfilehash: b2f2704a748627d9943943fa2fa7b1b7e9f3007f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447191"
---
# <a name="metadata"></a>Metadados

Há duas APIs para recuperar metadados em ADO.NET. Uma recupera metadados sobre os resultados da consulta. O outro recupera metadados sobre o esquema de banco de dados.

## <a name="query-result-metadata"></a>Metadados do resultado da consulta

Você pode recuperar metadados sobre os resultados de uma consulta usando o <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> método em `SqliteDataReader`. O retornado <xref:System.Data.DataTable> contém as seguintes colunas:

| Coluna             | Tipo    | Descrição                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | Boolean | True se a coluna de origem puder ser nula.                                    |
| `BaseCatalogName`  | String  | O nome do banco de dados da coluna de origem. Sempre nulo para expressões.    |
| `BaseColumnName`   | String  | O nome sem alias da coluna de origem. Sempre nulo para expressões.    |
| `BaseSchemaName`   | String  | Sempre nulo. O SQLite não dá suporte a esquemas.                              |
| `BaseServerName`   | String  | O caminho para o arquivo de banco de dados especificado na cadeia de conexão.         |
| `BaseTableName`    | String  | O nome da tabela da coluna de origem. Sempre nulo para expressões.       |
| `ColumnName`       | String  | O nome ou alias da coluna no conjunto de resultados.                        |
| `ColumnOrdinal`    | Int32   | O ordinal da coluna no conjunto de resultados.                              |
| `ColumnSize`       | Int32   | Sempre-1. Isso pode ser alterado em versões futuras `Microsoft.Data.Sqlite`do.   |
| `DataType`         | Tipo    | O tipo de dados padrão do .NET da coluna.                                 |
| `DataTypeName`     | String  | O tipo de dados do SQLite da coluna.                                       |
| `IsAliased`        | Boolean | True se o nome da coluna tiver um alias no conjunto de resultados.                     |
| `IsAutoIncrement`  | Boolean | True se a coluna de origem tiver sido criada com a palavra-chave AutoIncrement.     |
| `IsExpression`     | Boolean | True se a coluna se originar de uma expressão na consulta.            |
| `IsKey`            | Boolean | True se a coluna de origem fizer parte da chave primária.                     |
| `IsUnique`         | Boolean | True se a coluna de origem for exclusiva.                                      |
| `NumericPrecision` | Int16   | Sempre nulo. Isso pode ser alterado em versões futuras `Microsoft.Data.Sqlite`do. |
| `NumericScale`     | Int16   | Sempre nulo. Isso pode ser alterado em versões futuras `Microsoft.Data.Sqlite`do. |

O exemplo a seguir mostra como usar `GetSchemaTable` o para criar uma cadeia de caracteres de depuração que mostra metadados sobre um resultado:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

Por exemplo, essa consulta produziria a seguinte cadeia de caracteres de depuração:

```sql
SELECT id AS post_id,
       title,
       body,
       random() AS random
FROM post
```

```output
post.id AS post_id INTEGER PRIMARY KEY AUTOINCREMENT
post.title TEXT NOT NULL UNIQUE
post.body TEXT
(expression) AS random BLOB
```

## <a name="schema-metadata"></a>Metadados do esquema

Microsoft. Data. sqlite não implementa o método GetSchema em DbConnection. Em vez disso, você pode consultar diretamente as informações de esquema usando as instruções Table [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) e PRAGMA como [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) e [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).

Por exemplo, essa consulta recuperará metadados sobre todas as colunas no banco de dados.

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a>Veja também

* [Armazenamento do esquema do banco de dados SQL](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [Instruções PRAGMA](https://www.sqlite.org/pragma.html)
* [Tipos de dados](types.md)
