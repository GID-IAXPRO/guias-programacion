.PHONY: all clean check-deps

# Directory for generated PDFs
BUILD_DIR = build

# Find all Markdown files recursively
MARKDOWN_FILES = $(shell find ../doc/respuestas -name '*.md')

# Convert Markdown files to PDFs
PDF_FILES = $(patsubst ../doc/respuestas/%.md,$(BUILD_DIR)/%.pdf,$(MARKDOWN_FILES))

all: check-deps $(PDF_FILES)

check-deps:
	@echo "Checking Mermaid dependencies..."
	@command -v mmdc > /dev/null 2>&1 || { \
		echo "Mermaid CLI not found. Installing..."; \
		npm install -g @mermaid-js/mermaid-cli; \
	}

$(BUILD_DIR)/%.pdf: ../doc/respuestas/%.md | $(BUILD_DIR)
	@mkdir -p $(dir $@)  # Ensure the target directory exists
	@mkdir -p mermaid-images  # Ensure mermaid-images directory exists
	pandoc $< -o $@ --pdf-engine=tectonic --template=templates/eisvogel/eisvogel.latex --listings --filter ./pandoc-mermaid-mmdc

$(BUILD_DIR):
	mkdir -p $(BUILD_DIR)

clean:
	rm -rf $(BUILD_DIR)
	rm -rf mermaid-images