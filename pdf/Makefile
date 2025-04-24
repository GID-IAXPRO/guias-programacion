.PHONY: all clean

# Directory for generated PDFs
BUILD_DIR = build

# CSS file for styling
CSS_FILE = markdown-pdf.css

# Find all Markdown files recursively
MARKDOWN_FILES = $(shell find ../doc/respuestas -name '*.md')

# Convert Markdown files to PDFs
PDF_FILES = $(patsubst ../doc/respuestas/%.md,$(BUILD_DIR)/%.pdf,$(MARKDOWN_FILES))

all: $(PDF_FILES)

$(BUILD_DIR)/%.pdf: ../doc/respuestas/%.md | $(BUILD_DIR)
	@mkdir -p $(dir $@)  # Ensure the target directory exists
	pandoc $< -o $@ --pdf-engine=tectonic --css=$(CSS_FILE) --template=templates/eisvogel/eisvogel.latex --listings

$(BUILD_DIR):
	mkdir -p $(BUILD_DIR)

clean:
	rm -rf $(BUILD_DIR)