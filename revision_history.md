# 부록: 개정 내역

{\#history\_lesson}

## 부록: History Lesson

제가 파이썬을 처음 시작하게 된 계기는 전에 작성했던 'Diamond' 라는 소프트웨어를 좀 더 쉽게 설치할 수 있게 하기 위해 그것의 설치 프로그램을 작성하려고 했던 일이었습니다. 당시에 Qt 라이브러리를 사용하고 싶었는데, 이를 위해 파이썬과 펄 중 하나를 골라야 했었지요. 그래서 인터넷을 찾아보았는데 유명한 해커 [Eric S. Raymond 가 쓴 글](http://www.python.org/about/success/esr/)을 발견하게 되었습니다. 거기에는 파이썬이 어떻게 자신이 가장 좋아하는 프로그래밍 언어가 되었는지에 대해 적혀 있었지요. 또한 당시 Perl-Qt 바인딩에 비해 PyQt 바인딩이 좀 더 안정적이었기도 해서, 저는 파이썬을 선택하게 되었습니다.

다음으로 저는 좋은 파이썬 책이 있는지 찾아보기 시작했습니다. 그런데, 아무것도 찾을 수가 없었습니다! 몇 권의 오라일리\(O'Reilly\) 책을 찾았지만 이것들은 너무 비싸고 초보자를 위한 가이드이기보다는 레퍼런스 매뉴얼에 가까웠습니다. 그래서, 저는 파이썬 문서를 검색해보기 시작했습니다. 그렇지만 제가 찾은 것들은 너무 간략하거나 짧은 것들 뿐이었습니다. 저는 이런 문서들을 통해 기본적인 것들에 대한 도움을 받을 수 있었지만 파이썬에 대해 완전히 알 수는 없었습니다. 또 저는 프로그래밍을 전에 해 보았기 때문에 이런 짧은 문서들을 겨우겨우 이해해나갈 수 있었지만, 초보자에게는 불가능한 일이라는 것도 알게 되었습니다.

제가 파이썬을 처음 시작하고 6 개월정도 지난 뒤, 저는 레드햇 리눅스\(Red Hat Linux\) 9.0 을 설치하였는데 불현듯 KWord를 사용하여 파이썬에 대해 뭔가 적어보자는 생각이 떠올랐습니다. 처음에는 몇 장으로 시작했지만 곧 30 페이지 정도의 문서가 되었습니다. 그렇게 되니 좀 더 내용을 정리해서 책의 형태로 만들면 좀 더 유용하겠다는 생각을 했습니다. 그 후 _많은_ 재작성 끝에, 파이썬이라는 언어를 익히는 데 유용한 현재의 가이드를 만들 수 있었습니다. 저는 이 책이 저의 기여로 만들어졌지만 오픈 소스 공동체에 기여할 수 있기를 바랍니다.

이 책은 파이썬에 대한 저의 개인 노트에서 출발했고, 앞으로도 같은 방식으로 편집될 것입니다. 물론 다른 사람들이 이 책을 읽기 쉽게 하기 위한 노력 또한 계속 기울일 것이고요 :\)

또 오픈 소스 정신 안에서, 많은 열정적인 독자들의 제안과 비평 그리고 [피드백](https://github.com/byte-of-python-korean/a-byte-of-python/tree/5ededa01e8509a940d68be0d7c9dd0962287a9c5/who_reads_bop.md#who_reads_bop) 을 통해 이 책이 지금까지 성장할 수 있었음을 알립니다.

## 부록: 변경 기록

* 이 책은 {localdate} 에 [AsciiDoctor](http://www.asciidoctor.org) {asciidoctor-version} 를 이용하여

  자동으로 생성되었습니다.

* 이 책은 2014년 3월 ~ 4월 사이에 마지막으로 변경되었으며,

  [Emacs 24](http://swaroopch.com/2013/10/17/emacs-configuration-tutorial/) 의

  [adoc-mode](https://github.com/sensorflo/adoc-mode/wiki) 를 이용하여

  [Asciidoc](http://asciidoctor.org/docs/what-is-asciidoc/) 으로 변환되었습니다.

* 2008년에 이 책은 파이썬 3.0 에 대응하도록 변경되었습니다만 \(당시 3.0 에 대응하는 몇 안되는 책 중

  하나였습니다\), 현재는 다시 파이썬 2에 대응하도록 변경되었습니다. 그 이유는 자신의

  시스템에 기본으로 설치되어 있는 파이썬 2와 직접 설치하고 설정해야 하는 파이썬 3 사이에서

  혼란을 겪는 독자들이 많았기 때문인데, 이는 새로 설치한 파이썬을 설정하는 과정을 설명하는

  여러 다른 문서들이 파이썬 2를 기준으로 작성되어 있기 때문입니다. 그래서 저는 괜히 파이썬 3을 고집해서

  독자들을 괴롭히고 있는 것은 아닌가 하는 고민에 빠졌고 또 파이썬 2 나 3 중 하나만

  잘 배워 두어도 독자들에게는 충분히 유용할 수 있다는 생각에, 다시 파이썬 2를 선택하게 되었습니다.

이 책은 여러분과 같은 독자들의 도움이 필요합니다. 책을 읽다가 설명이 좋지 않거나, 부족하거나 또는 잘못된 부분이 있다면 지적해 주시기 바랍니다. 코멘트나 제안이 있으실 경우 {contact}\[이 책의 저자\] 나 mailto:pjb7687@gmail.com\[역자\] 에게 연락해 주시기 바랍니다.

{\#revision\_history}

## 부록: 리비전 기록

* 3.0

  \*\* 31 Mar 2014

  \*\* Rewritten using [AsciiDoc](http://asciidoctor.org/docs/what-is-asciidoc/) and

     [adoc-mode](https://github.com/sensorflo/adoc-mode/wiki).

* 2.1

  \*\* 03 Aug 2013

  \*\* Rewritten using Markdown and [http://jblevins.org/projects/markdown-mode/\[Jason](http://jblevins.org/projects/markdown-mode/[Jason) Blevins'

     Markdown Mode\]

* 2.0

  \*\* 20 Oct 2012

  \*\* Rewritten in [Pandoc format](http://johnmacfarlane.net/pandoc/README.html), thanks to my wife

     who did most of the conversion from the Mediawiki format

  \*\* Simplifying text, removing non-essential sections such as `nonlocal` and metaclasses

* 1.90

  \*\* 04 Sep 2008 and still in progress

  \*\* Revival after a gap of 3.5 years!

  \*\* Rewriting for Python 3.0

  \*\* Rewrite using [MediaWiki](http://www.mediawiki.org) \(again\)

* 1.20

  \*\* 13 Jan 2005

  \*\* Complete rewrite using [Quanta+](https://en.wikipedia.org/wiki/Quanta_Plus) on

     [Fedora](http://fedoraproject.org/) Core 3 with lot of corrections and updates. Many new

     examples. Rewrote my DocBook setup from scratch.

* 1.15

  \*\* 28 Mar 2004

  \*\* Minor revisions

* 1.12

  \*\* 16 Mar 2004

  \*\* Additions and corrections

* 1.10

  \*\* 09 Mar 2004

  \*\* More typo corrections, thanks to many enthusiastic and helpful readers.

* 1.00

  \*\* 08 Mar 2004

  \*\* After tremendous feedback and suggestions from readers, I have made significant revisions to

     the content along with typo corrections.

* 0.99

  \*\* 22 Feb 2004

  \*\* Added a new chapter on modules. Added details about variable number of arguments in functions.

* 0.98

  \*\* 16 Feb 2004

  \*\* Wrote a Python script and CSS stylesheet to improve XHTML output, including a

     crude-yet-functional lexical analyzer for automatic VIM-like syntax highlighting of the

     program listings.

* 0.97

  \*\* 13 Feb 2004

  \*\* Another completely rewritten draft, in DocBook XML \(again\). Book has improved a lot - it is

     more coherent and readable.

* 0.93

  \*\* 25 Jan 2004

  \*\* Added IDLE talk and more Windows-specific stuff

* 0.92

  \*\* 05 Jan 2004

  \*\* Changes to few examples.

* 0.91

  \*\* 30 Dec 2003

  \*\* Corrected typos. Improvised many topics.

* 0.90

  \*\* 18 Dec 2003

  \*\* Added 2 more chapters. [OpenOffice](https://en.wikipedia.org/wiki/OpenOffice) format with

     revisions.

* 0.60

  \*\* 21 Nov 2003

  \*\* Fully rewritten and expanded.

* 0.20

  \*\* 20 Nov 2003

  \*\* Corrected some typos and errors.

* 0.15

  \*\* 20 Nov 2003

  \*\* Converted to [DocBook XML](https://en.wikipedia.org/wiki/DocBook) with XEmacs.

* 0.10

  \*\* 14 Nov 2003

  \*\* Initial draft using [KWord](https://en.wikipedia.org/wiki/Kword).

