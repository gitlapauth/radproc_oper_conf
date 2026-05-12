
.PHONY := preprocess
.DEFAULT_GOAL := all
all: html pdf

## list source files
markdowns := $(shell find -name "*.md" | sort -V)

## pre pandoc run
preprocess: .markdowncontent
.markdowncontent: $(markdowns) .pre_process.sh
	./.pre_process.sh $(markdowns)

watchfiles := Makefile .markdowncontent _index.yaml

# Pandoc options
PANDOC_FLAGS := --standalone                            \
								--lua-filter      include-files.lua     \
                --highlight-style pygments              \
                --metadata        author="$(AUTHOR)"    \
                --metadata        title="$(DIRNAME)"    \
                --template        $(TEMPLT)             \
                --toc                                   \
                --webtex


MARKDN_FLAGS := --standalone                            \
                --metadata        title="$(DIRNAME)"    \
                --metadata        author="$(AUTHOR)"    \
                --webtex

TARGET = ./radproc_Journal.pdf
pdf: $(TARGET)
$(TARGET): $(watchfiles)
	-pandoc                           \
	  --from            markdown      \
	  --highlight-style pygments      \
	  --lua-filter      .columns.lua  \
	  --metadata-file   _index.yaml   \
	  --out             '$@'          \
	  --pdf-engine      xelatex       \
	  --standalone                    \
	  --to              pdf           \
	  --toc                           \
	  .markdowncontent


TARGET = ./radproc_Journal.html
html: $(TARGET)
$(TARGET): Makefile .markdowncontent .pre_process.sh
	-pandoc                           \
	  --embed-resources               \
	  --from            markdown      \
	  --lua-filter      .columns.lua  \
	  --mathjax                       \
	  --metadata-file   _index.yaml   \
	  --out             '$@'          \
	  --standalone                    \
	  --template        .easy-pandoc-templates-master/html/uikit.html \
	  --to              html          \
	  --toc                           \
	  .markdowncontent


