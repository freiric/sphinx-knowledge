Gitit 
==========

.. code-block::


   ContentTransformer
   pandocToHtml
			 , writerTemplate = "$if(toc)$<div id=\"TOC\">\n$toc$\n</div>\n$endif$\n$body$"

I would say, you cannot customize the html of tabs or toc without modifying the code.
The html code for tabs is set together in Network.Gitit.Layout.filledPageTemplate. The html code for the toc is computed in pandoc, in Text.Pandoc.Writers.HTML.pandocToHtml (delegating to tableOfContents).
