FO_FILE=$(FO_DIR)/$(DOC_NAME)-$(VERSION)-$(DOC_TYPE_NAME)-$(LANG).fo
PDF_FILE=$(PDF_DIR)/$(DOC_NAME)-$(VERSION)-$(DOC_TYPE_NAME)-$(LANG).pdf
SCHEMA_REF=schema-reference.xml
BOOKML_CFG=$(BOOKML_CFG_DIR)/$(LANG).xml


all: $(PDF_FILE)

$(PDF_FILE): $(FO_FILE)
	$(FOP) -c $(KF4FOP)/fop-conf.xml -fo $(FO_FILE) -pdf $(PDF_FILE)

$(FO_FILE): $(FO_XSL) $(DOC_TYPE_NAME).xml $(SCHEMA_REF) $(BOOKML_CFG)
	$(XMLLINT) $(XMLLINT_PARAM) manual.xml
	$(XSLTPROC) $(XSLT_PARAM) --stringparam config "$(BOOKML_CFG)" $(FO_XSL) manual.xml > $(FO_FILE)

$(SCHEMA_REF): $(SCHEMA_REFERENCE_XSL) $(SCHEMA_RNG)
	$(XSLTPROC) $(XSLT_PARAM) --stringparam lang "$(LANG)" --stringparam schema-name "$(SCHEMA_NAME)" $(SCHEMA_REFERENCE_XSL) $(SCHEMA_RNG) > $(SCHEMA_REF)

clean:
	$(RM) $(SCHEMAREF)

.PHONY: all clean


