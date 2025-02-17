Changelog
==========

<!--

Newest changes should be on top.

What should be mentioned (in order):
+ Optional: In **bold**. A backported notice.
+ A summary of the change.
+ A link to the PR for further reading.
+ Credit where credit is due by mentioning the github account.

Keep the changelog pleasant to read in the text editor:
+ Empty line between changes.
+ Newline between summary and link+credit.
+ Properly indent blocks.
-->

version 1.2.0
---------------------------

+ Introduced the concept of "scoped types" to support the use of object-like values within the `hints` section while still keeping the `Object` type as deprecated.

+ Added new task `requirements` and `hints` sections (#540 and #541), and deprecated the `runtime` section

+ Added new workflow `hints` section (#543), and moved `allowNestedInputs` from workflow `meta` to `hints`

+ Deprecated the previously allowed behavior implied by setting `allowNestedInputs: true` where required task/subworkflow inputs could be left unsatisfied. Now all inputs either need to have a default value or have their value specified in the call inputs. Only optional task/subworkflow inputs that are not explicitly set in the call inputs may have their value set at runtime if the `allow_nested_inputs` hint is `true`.

+ Added the ability to access the actual values of `requirements`, `meta`, and `parameter_meta` at runtime.

+ Added `fpga` requirement and reserved hint for requesting FPGA resources.

+ Added `disks` and `gpu` reserved hints for requesting specific resources.

+ Added `contains_key` function to standard library. [PR 603](https://github.com/openwdl/wdl/pull/603)

+ Added exponentiation operator (`**`).

+ Added `find`, and `matches` functions.

+ Added `chunk` function for chunking an array into sub-arrays.

+ Add `parameter_meta` section to struct definition.

+ Relaxed the requirements on coercing object/map to struct - extra keys are allowed and ignored. Note that this *may* constitute a breaking change if you rely on a task to fail when coercing an object/map with extra keys.

+ Added `join_paths` function to join two or more paths.

+ Added allowance for conversion between `Struct` types when certain criteria are met.

+ Generalized `size` function to take any compound value.

+ Added optional `default` parameter to `select_first`.

+ Generalized `length` function to also accept `Map`, `Object`, and `String` arguments.

+ Added multi-line strings. [PR 602](https://github.com/openwdl/wdl/pull/602)

+ Added the `Array[String] keys(Struct|Object)` function variant for getting the member names for a struct or object.

+ Added `values` function for getting the values from a `Map`.

+ Added parameters to `read_tsv` that enable it to read field names from a header row or an `Array[String]` and return an `Array[Object]`. [PR 627](https://github.com/openwdl/wdl/pull/627)

+ Added `contains` function for determining whether an array contains a specified value.

+ Clarify how inputs with defaults are implicitly optional
  [PR 464](https://github.com/openwdl/wdl/pull/464) by @mlin

+ Make `input:` optional in call bodies.
  [PR 524](https://github.com/openwdl/wdl/pull/524) by @mlin.

+ Added `Directory` type. [PR 641](https://github.com/openwdl/wdl/pull/641)

+ Added clarification that input files and directories should be treated as read-only. [PR 642](https://github.com/openwdl/wdl/pull/642)

+ Added JSON extended file/directory input/output format. [PR 643] (https://github.com/openwdl/wdl/pull/643)

+ Clarified that local paths are always used when evaluating input/private/command expressions.

+ Clarified the meaning of a remote parent folder for the purposes of localization.

+ Clarified that accessing a non-existent member of an object, struct, or call is an error.

version 1.1.2
---------------------------

+ State that `Union` is also the type of some `runtime` attributes.

+ Remove some syntax sections that were missed in 1.1.1.

+ Clarify short-circuiting of boolean expressions (#199)

+ Added requirement for tests to the RFC

+ Clarifies number of sections allowed within `task` and `workflow` blocks.
  [PR 598](https://github.com/openwdl/wdl/pull/598) by @claymcleod

+ Clarified that `read_bool` is case-insensitive, and added an example.

version 1.1.1
---------------------------

+ Applied [Errata](https://github.com/openwdl/wdl/blob/main/versions/1.1/Errata.md) to the 1.1.0 spec.

+ Updated most examples to adhere to the new specification for WDL tests.

+ Added missing `File` and `version` keywords to the list of reserved words.

+ Added new sections or materially expanded existing sections:
  + "Limited exceptions" to type coercion rules
  + "Static Analysis and Dynamic Evaluation"
  + "Task Input Localization"
  + "Expression Placeholders" under "Command Section"
  + Hidden types

+ Reformatted all tables.

+ Reorganzied the standard library.

+ Provided codespell configuration and workflow to catch typos.
  [PR 530](https://github.com/openwdl/wdl/pull/530) by @yarikoptic.

+ Fixed typos, thanks to @yarikoptic, @sejyoti, @mmterpstra, @j23414, @jdavcs, @beukueb, @notestaff, @alberto-mg, @mperf!

version 1.1.0
---------------------------

+ Added [Errata](https://github.com/openwdl/wdl/blob/main/versions/1.1/Errata.md).
 
+ Clarified that the `sub` function requires a POSIX Extended Regular Expression (ERE).
  [PR 243](https://github.com/openwdl/wdl/pull/243) by @rhpvorderman

+ Added syntax for struct literals.
  [PR 297](https://github.com/openwdl/wdl/pull/297) by @patmagee

+ Added engine functions for `min` and `max`.
  [PR 304](https://github.com/openwdl/wdl/pull/304) by @pshapiro

+ Added section on file outputs including optional outputs.
  [PR 310](https://github.com/openwdl/wdl/pull/310) by @jtratner

+ Added reserved keys, explicit formats, and default values for runtime attributes and hints.
  [PR 315](https://github.com/openwdl/wdl/pull/315) by @patmagee

+ Namespacing has been clarified.
  [PR 340](https://github.com/openwdl/wdl/pull/340) by @DavyCats

+ Abbreviated syntax for call inputs bound to workflow-scoped values by name:
  `{input: x, y=b, z}` is shorthand for `{input: x=x, y=b, z=z}`
  [PR 365](https://github.com/openwdl/wdl/pull/365) by @mlin

+ Write a specification for unsatisfied task inputs and nested optional inputs.
  [PR 359](https://github.com/openwdl/wdl/pull/359) by @rhpvorderman
  
+ Adds an engine function for joining arrays of strings. 
  [PR 229](https://github.com/openwdl/wdl/pull/229) and [PR 368](https://github.com/openwdl/wdl/pull/366) 
  by @EvanTheB and @illusional.

+ Added an engine function for adding a suffix to an array of primitives as well
  as well as `quote` and `squote` engine functions.
  [PR 362](https://github.com/openwdl/wdl/pull/362) @patmagee

+ Added a required input and output format for workflow engines.
  [PR 357](https://github.com/openwdl/wdl/pull/357)

+ The input specification has been clarified.
  [PR 314](https://github.com/openwdl/wdl/pull/314) by @geoffjentry.

+ Added a list of keywords that can not be used as identifiers.
  [PR 307](https://github.com/openwdl/wdl/pull/307) by @mlin.

+ Empty call blocks have been clarified.
  [PR 302](https://github.com/openwdl/wdl/pull/302) by @aednichols.

+ Optional and non-empty type constraints have been clarified.
  [PR 290](https://github.com/openwdl/wdl/pull/290) by @mlin.

+ The way comments work has been clarified.
  [PR 277](https://github.com/openwdl/wdl/pull/277) by @patmagee.

+ Implement string escapes in the Hermes grammar.
  [PR 272](https://github.com/openwdl/wdl/pull/272) by @cjllanwarne.

+ Added `None` for explicitly stating that an optional variable is not defined.
  [PR 263](https://github.com/openwdl/wdl/pull/263) by @rhpvorderman.

+ **Backported to 1.0**: Fix a bug in the grammar regarding unescaped strings.
  [PR 253](https://github.com/openwdl/wdl/pull/253) and
  [PR 255](https://github.com/openwdl/wdl/pull/255) by @aednichols.

+ WDL Files should be encoded in UTF-8 now. String definitions have been
  clarfied.
  [PR 247](https://github.com/openwdl/wdl/pull/247) by @EvanTheB.

+ The version `statement` can now be the first *non-comment* statement. So it
  can be stated below a license header for example.
  [PR 245](https://github.com/openwdl/wdl/pull/245) by @ffinfo.

+ Added a `keys` function to get an array of keys from a map.
  [PR 244](https://github.com/openwdl/wdl/pull/244) by @ffinfo.

+ Several bugs in the grammar have been fixed.
  [PR 238](https://github.com/openwdl/wdl/pull/238) and
  [PR 240](https://github.com/openwdl/wdl/pull/240) by @cjllanwarne.

+ Type conversions and meanings have been clarified.
  [PR 235](https://github.com/openwdl/wdl/pull/235) by @EvanTheB.

+ **Backported to 1.0**: Imports are now relative to their current location.
  [PR 220](https://github.com/openwdl/wdl/pull/220) by @geoffjentry.

+ Added conversion functions `as_pairs` and `as_map` to convert between
  `Array[Pair[X,Y]]` and `Map[X,Y]`.
  [PR 219](https://github.com/openwdl/wdl/pull/219) by @DavyCats.

+ Add an `after` keyword to run a task after other tasks.
  [PR 162](https://github.com/openwdl/wdl/pull/162) by @cjllanwarne.

version 1.0.0
---------------------------
+ Rename lexer to `WdlV1Lexer`
+ Rename parser to `WdlV1Parser`
+ Rename `WdlComments` channel to `COMMENTS`
+ Remove `SkipChannel`
+ Rename `COMMENT` -> `LINE_COMMENT`, emit comments to `COMMENTS` channel
+ Add `Meta` mode for parsing meta sections
+ Parse whitespace between `command` and opening `{`/`<<<` within `Command` mode, so that it is emitted to the `HIDDEN` channel
+ Ignore trailing commas
+ Formatting -
    * use two spaces always for indentation
    * always wrap statements (i.e. always put opening ':' and closing ';' on newlines)
    * always use PascalCase for tokens within lexer modes

draft-2
---------------------------

+ Added ANTLR4 grammar

