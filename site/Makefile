BUNDLER_VERSION = 1.15.1
BUNDLE = bundle _${BUNDLER_VERSION}_
JEKYLL = ${BUNDLE} exec jekyll

dev:
	code .
	open http://localhost:4000
	make serve

clean:
	rm -rf _site

setup:
	gem install bundler \
		-v ${BUNDLER_VERSION} \
		--no-rdoc \
		--no-ri
	NOKOGIRI_USE_SYSTEM_LIBRARIES=true ${BUNDLE} install \
		--path vendor/bundle

build: clean
	${JEKYLL} build \
		--config _config.yml

javadoc-gen:
	scripts/javadoc-gen.sh

serve: build
	${JEKYLL} serve \
		--incremental \
		--config _config.local.yml

publish: javadoc-gen build
