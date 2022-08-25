.DEFAULT_GOAL := help
.PHONY: tag build

version=$(shell cat .version)

tag: ## Tag git repo
	git tag -a ${version} -m "Bump ${version}"
	git push origin main --follow-tags

build: ## Build Docker image
	echo "[${version}]"
	docker build --tag ghrc.io/thinkinglabs/packer:${version} .

help:
	@grep -h -E '^[a-zA-Z0-9_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'
