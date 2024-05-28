# Confluence to Markdown converter
(that works right now but probably not in a few months time, but if you tell us we'll fix it!)

## Recommendation
Outline Wiki has a rather good Confluence HTML import and supports exporting to markdown. Rather than using _this_ project, it is possible to get a higher quality conversion to markdown by self-hosting an Outline Wiki, importing from COnfluence HTML and bulk exporting to Markdown. [Link to Outline Docs](https://docs.getoutline.com/s/guide/doc/confluence-import-UGCiYLYgBd)

## Requirements

### You will require a HTML export of the Confluence space using the default Confluence export tool. This is found at:
`https://<YOUR_ATLASSIAN_DOMAIN>.atlassian.net/wiki/spaces/exportspacewelcome.action?key=<PROJECT_KEY>`

Setup:
Clone and run `yarn` in root directory

## Usage

It's a good idea to create an 'output' folder somewhere to target with the `pathResult` parameter (where the output files will go)

In the converter's directory:

```
yarn start <inputPath> <outputPath> <confluenceUrl> <runPostProcessScript> <verboseLogging>
```
e.g
`yarn start /Users/<User>/Documents/targetfoldername /Users/<User>/Documents/outputfoldername https://<YOUR_ATLASSIAN_DOMAIN>.atlassian.net/wiki/spaces/ true false`

### Parameters

parameter | description
--- | ---
`<inputPath>` | File or directory to convert with extracted Confluence export
`<outputPath>` | Directory to where the output will be generated to.
`<confluenceUrl>` | Confluence URL to be used when updating links. Must include trailing slash, 'wiki' and 'spaces' url paths (see example)
`<runPostProcessScript>` | OPTIONAL 'true' to run the file location cleanup and link fix script, 'false' or omitted to not run the script
`<verboseLogging>` | OPTIONAL 'true' to log in detail, 'false' or omitted to run with default minimal logging

### Optional

To run the Post Process Script directly:

`bash <pathToUpdateLinksScript> <outputPath> <spaceName>`

When the script is run from the node project, the space name is derived from the root index.html "Space Detail" "Key" field.

### Parameters

| parameter                   | description                                                  |
| --------------------------- | ------------------------------------------------------------ |
| `<pathToUpdateLinksScript>` | Absolute path to `update-links.sh` in the `./src` folder of the project |
| `<outputPath>`              | Directory to the markdown files that need to be processed    |
| `<spaceName>`               | Name of the root confluence space                            |
| `<confluenceUrl>`           | Confluence URL to be used when updating links. Must include trailing slash `/`                      |

## Recognition

### Original Project and packages:

Eric White / Meridus for the original [Confluence to Markdown](https://github.com/meridius/confluence-to-markdown)

Dom Christie and community for [Turndown](https://github.com/mixmark-io/turndown)

Guyplusplus for [Turndown Plugin Confluence to GFM](https://github.com/guyplusplus/turndown-plugin-confluence-to-gfm)

Arch-nemesis: [Markdown to Confluence uploader](https://github.com/lanyonm/markdown-to-confluence-uploader)

### Current modifications
Node.js project changes: John Briggs [jdeb9](https://github.com/jdeb9)

Bash script post-processing: Michael Ruigrok [michaelruigrok](https://github.com/michaelruigrok)
