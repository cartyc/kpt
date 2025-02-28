# Copyright 2022 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# GCP project to use for development
GCP_PROJECT_ID ?= $(shell gcloud config get-value project)
IMAGE_TAG ?= latest
IMAGE_REPO ?= gcr.io/$(GCP_PROJECT_ID)
IMAGE_NAME ?= porch-controllers

.PHONY: push-image
push-image:
	cd ../..; docker buildx build --push --tag $(IMAGE_REPO)/$(IMAGE_NAME):$(IMAGE_TAG) -f porch/controllers/Dockerfile .

.PHONY: build-image
build-image:
	cd ../..; docker buildx build --load --tag $(IMAGE_REPO)/$(IMAGE_NAME):$(IMAGE_TAG) -f porch/controllers/Dockerfile .
