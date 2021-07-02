# @tencent/flink-sql-format

A fork of [SQL Formatter](https://github.com/zeroturnaround/sql-formatter) with some extra bug fixes and features. 

## Install

Get the latest version from NPM:

```shell
npm install @tencent/flink-sql-format
```

## Usage

```javascript
import sqlFormatter from '@tencent/flink-sql-format';

console.log(sqlFormatter.format('SELECT * FROM table1'));
```

This will output:

```sql
SELECT
  *
FROM
  table1
```

You can also pass in configuration options:

```javascript
sqlFormatter.format('SELECT *', {
  language: 'n1ql', // Defaults to "sql"
  indent: '    ', // Defaults to two spaces,
  uppercase: true, // Defaults to false
  linesBetweenQueries: 2 // Defaults to 1
});
``` 

### Placeholders replacement

```javascript
// Named placeholders
sqlFormatter.format("SELECT * FROM tbl WHERE foo = @foo", {
  params: {foo: "'bar'"}
}));

// Indexed placeholders
sqlFormatter.format("SELECT * FROM tbl WHERE foo = ?", {
  params: ["'bar'"]
}));
```

Both result in:

```sql
SELECT
  *
FROM
  tbl
WHERE
  foo = 'bar'
```

## Usage without NPM

If you don't use a module bundler, clone the repository, run `npm install` and grab a file from `/dist` directory to use inside a `<script>` tag.
This makes SQL Formatter available as a global variable `window.sqlFormatter`.

## Contributing

```shell
# run linter and tests
npm run check
```

...and you're ready to poke us with a pull request.

## License

[MIT](https://github.com/zeroturnaround/sql-formatter/blob/master/LICENSE)

[php library]: https://github.com/jdorn/sql-formatter
[standard sql]: https://en.wikipedia.org/wiki/SQL:2011
[couchbase n1ql]: http://www.couchbase.com/n1ql
[ibm db2]: https://www.ibm.com/analytics/us/en/technology/db2/
[oracle pl/sql]: http://www.oracle.com/technetwork/database/features/plsql/index.html
