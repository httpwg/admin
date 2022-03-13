_This page gives advice about tools and formats for document editors._

**See also:**

* The [Style Guide](Style-Guide)
* [Post Working Group Process](https://github.com/httpwg/wiki/wiki/Editors:--Post-Working-Group-Process) guidelines

## Getting Started

Once you've been appointed as an editor by the Chairs, your first task will be to get a `-00` draft published. 

1. Send your GitHub username to the Chairs if you're not already a member of the `Editors` team, and they'll add you.
2. Create a PR with your new draft added to the root directory of the repo, with a name in the format `draft-ietf-httbis-NAME.md` (assuming you're using Markdown; see "Editing Formats" below).
3. Ask for review by the Chairs to make sure everything is in order.
4. Once it's merged by the Chairs, follow the instructions in `SUBMITTING.md` to publish your `-00`.

Usually, a `-00` draft has few, if any, differences from the draft that was adopted, to serve as a stable basis for future diffs. By convention, however, we add a section to the top of our drafts with links for the convenience of readers; e.g.,

~~~ markdown
--- note_Note_to_Readers

*RFC EDITOR: please remove this section before publication*

Discussion of this draft takes place on the HTTP working group mailing list
(ietf-http-wg@w3.org), which is archived at <https://lists.w3.org/Archives/Public/ietf-http-wg/>.

Working Group information can be found at <https://httpwg.org/>; source
code and issues list for this draft can be found at
<https://github.com/httpwg/http-extensions/labels/cache-header>.
~~~

## Editing Formats

The canonical format for RFCs is now XML. However, we recommend authoring in Markdown -- specifically, [kramdown-rfc2629](https://github.com/cabo/kramdown-rfc2629). That format is not only easier to edit, it's also easier for the community to review (think of the diffs) and provide input to in the form of PRs.

See [this cheatsheet](https://github.com/cabo/kramdown-rfc2629/wiki/Syntax) for details of that syntax.

You can of course use any text editor; however, we encourage using one that supports [EditorConfig](https://editorconfig.org).

## Repo Etiquette

You can use PRs to manage your edits, or you can commit directly to the `main` branch. Please refrain from making edits to drafts other than your own, even if you feel they are helpful. Of course, you can propose changes with PRs, just as any other participant can.

Likewise, please refrain from making edits to the repository administrative files (e.g., `README.md`), adding labels, etc. without consulting the Chairs.

## CI

We use [Martin Thomson's I-D template](https://github.com/martinthomson/i-d-template) for most of our specification repos. It uses CI to automatically build text and HTML versions of the draft(s) on the `gh-pages` branch so that they can be referenced. 

Note that on the `http-extensions` repo, `make lint` will run [rfc-http-validate](https://github.com/mnot/rfc-http-validate). That will assure that all `artwork` and `sourcecode` blocks with a type of `http-message` are proper HTTP messages -- either complete or partial (e.g., just headers).

In the markdown syntax, you can flag sections for validation like this:

    ~~~ http-message
    Foo-Header: bar
    Bar-Header: baz
    ~~~

If you use [Structured Fields](https://httpwg.org/specs/rfc8941.html), add the fields your specification defines to `sf.json` to validate their basic syntax.

