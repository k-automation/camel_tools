![alt text](camel_logo.png "CAMeL logo")

# CAMeL Tools

## Introduction
A suite of morphological analysis and disambiguation tools for Arabic developed by the [CAMeL Lab](https://nyuad.nyu.edu/en/research/faculty-research/camel-lab.html) at [New York University Abu Dhabi](http://nyuad.nyu.edu/).


## Installation
At the moment, CAMeL Tools can only be installed from source by following the
instructions below.

```bash
# Download the repo
git clone https://github.com/owo/camel_tools.git
cd camel_tools

# Install CAMeL Tools and all dependencies
pip install .
```


## Usage
CAMeL Tools are a set of command line interface (CLI) tools as well as a set
of Python libraries. This section will help you get started with both.

### CLI Tools
This section will list all the CLI tools that come bundled with CAMeL Tools and
will explain their usage.

#### camel_transliterate
The `camel_transliterate` tool allows you to transliterate text from one form
to another using one of the builtin transliteration schemes.
Below is the usage information that can be generated by running
`camel_transliterate --help`.
```
Usage:
    camel_transliterate (-s SCHEME | --scheme=SCHEME)
                        [-o OUTPUT | --output=OUTPUT] [FILE]
    camel_transliterate (-l | --list)
    camel_transliterate (-v | --version)
    camel_transliterate (-h | --help)

Options:
  -s SCHEME --scheme          Scheme used for transliteration.
  -o OUTPUT --output=OUTPUT   Output file. If not specified, output will be
                              printed to stdout.
  -l --list                   Show a list of available transliteration schemes.
  -h --help                   Show this screen.
  -v --version                Show version.
```

Below is a list of currently available transliteration schemes.
```
ar2bw        Arabic to Buckwalter
ar2safebw    Arabic to Safe Buckwalter
ar2xmlbw     Arabic to XML Buckwalter
ar2hsb       Arabic to Habash-Soudi-Buckwalter
bw2ar        Buckwalter to Arabic
safebw2ar    Safe Buckwalter to Arabic
xmlbw2ar     XML Buckwalter to Arabic
hsb2ar       Habash-Soudi-Buckwalter to Arabic
arclean      Clean Arabic text
```
##### Notes on schemes
Below is a reference conversion table of Arabic to Buckwalter (BW), Safe
Buckwalter (Safe BW), XML Buckwalter (XML BW),
and Habash-Soudi-Buckwalter (HSB) transliteration schemes.

The transliteration schemes `ar2bw`, `ar2safebw`, `ar2xmlbw`, `ar2hsb`,
`bw2ar`, `safebw2ar`, `xmlbw2ar`, and `hsb2ar` all use the conversion table
below for transliteration. Input characters not listed in the table below
are output as they appear without any transliteration.

| Unicode | Arabic | BW | Safe BW | XML BW | HSB |
|:------:|:------:|:--:|:-------:|:------:|:----:|
| \u0621 | ء      | '  | C       | '      | '    |
| \u0622 | آ      | \| | M       | \|     | Ā    |
| \u0623 | أ      | >  | O       | O      | Â    |
| \u0624 | ؤ      | &  | W       | W      | ŵ    |
| \u0625 | إ      | <  | I       | I      | Ă    |
| \u0626 | ئ      | }  | Q       | }      | ŷ    |
| \u0627 | ا      | A  | A       | A      | A    |
| \u0628 | ب      | b  | b       | b      | b    |
| \u0629 | ة      | p  | p       | p      | ħ    |
| \u062A | ت      | t  | t       | t      | t    |
| \u062B | ث      | v  | v       | v      | θ    |
| \u062C | ج      | j  | j       | j      | j    |
| \u062D | ح      | H  | H       | H      | H    |
| \u062E | خ      | x  | x       | x      | x    |
| \u062F | د      | d  | d       | d      | d    |
| \u0630 | ذ      | *  | V       | *      | ð    |
| \u0631 | ر      | r  | r       | r      | r    |
| \u0632 | ز      | z  | z       | z      | z    |
| \u0633 | س      | s  | s       | s      | s    |
| \u0634 | ش      | $  | c       | $      | š    |
| \u0635 | ص      | S  | S       | S      | S    |
| \u0636 | ض      | D  | D       | D      | D    |
| \u0637 | ط      | T  | T       | T      | T    |
| \u0638 | ظ      | Z  | Z       | Z      | Ď    |
| \u0639 | ع      | E  | E       | E      | ς    |
| \u063A | غ      | g  | g       | g      | γ    |
| \u0640 | ـ      | _  | _       | _      | _    |
| \u0641 | ف      | f  | f       | f      | f    |
| \u0642 | ق      | q  | q       | q      | q    |
| \u0643 | ك      | k  | k       | k      | k    |
| \u0644 | ل      | l  | l       | l      | l    |
| \u0645 | م      | m  | m       | m      | m    |
| \u0646 | ن      | n  | n       | n      | n    |
| \u0647 | ه      | h  | h       | h      | h    |
| \u0648 | و      | w  | w       | w      | w    |
| \u0649 | ى      | Y  | Y       | Y      | ý    |
| \u064A | ي      | y  | y       | y      | y    |
| \u064B | ً      | F  | F       | F      | ã    |
| \u064C | ٌ      | N  | N       | N      | ũ    |
| \u064D | ٍ      | K  | K       | K      | ĩ    |
| \u064E | َ      | a  | a       | a      | a    |
| \u064F | ُ      | u  | u       | u      | u    |
| \u0650 | ِ      | i  | i       | i      | i    |
| \u0651 | ّ      | ~  | ~       | ~      | ~    |
| \u0652 | ْ      | o  | o       | o      | .    |
| \u0670 | ٰ      | \` | e       | \`     | á    |
| \u0671 | ٱ      | {  | L       | {      | Ä    |
| \u067E | پ      | P  | P       | P      | p    |
| \u0686 | چ      | J  | J       | J      | c    |
| \u06A4 | ڤ      | V  | B       | V      | v    |
| \u06AF | گ      | G  | G       | G      | g    |


The `arclean` scheme cleans Arabic text by:
  - Deleting characters that are not in Arabic, ASCII, or Latin-1.
  - Converting all spacing characters to an ASCII space character.
  - Converting Indic digits into Arabic digits.
  - Converting extended Arabic letters into basic Arabic letters.
  - Converting 1-char presentation froms into simple basic forms.

### Python Library


## Contribute
If you would like to contribute to CAMeL Tools, please read the
[CONTRIBUTE.md](./CONTRIBUTING.md) file.
