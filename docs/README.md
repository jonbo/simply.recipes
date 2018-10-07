# Simply Recipe Schema API (v1) Documentation

> v1 is incomplete, additional keys may be added to satisify certain conditions better. v2 will be created only if breaking changes.

- **version** : (required integer)
  > The API version
- **command** : (required object)

  - **name**: (required string)
    > The name of the commandline program
  - **version**: (optional string)
    > The version of the commandline program
  - **arguments** : (required []object)

    - **name** : (required string)

      > The argument name to show

      > if not unique must provide **id**

    - **id** : (optional unique string default=**name**)
      > The **name** will serve as an identifer by default.
    - **description** : (optional string)
    - **arg** : (required []string)
      > The command argument string(s) ["-e","--example"]
    - **type** : (optional string default="void")
      > available types: "void", "string", "option", "number"
    - **defaultValue** : (optional string)
    - **optionValues** : (optional []string)
      > if **type** is "option", this is required
    - **allowed** : (optional object)

      > if not provided, the default is allow

      > if provided any of the keys below, being falsly is to disallow

      > the strings below must be a valid argument **id**

      - **if** : (optional []string)
        > if all are truthy
      - **ifNot** : (optional []string)
        > if all are falsey
      - **ifAny** : (optional []string)
        > if any are truthy
      - **ifNotAny** : (optional []string)
        > if any are falsey

    - **repeat** : (optional boolean default=false)
      > if an argument can be used more than once
