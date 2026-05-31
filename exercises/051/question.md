# Question 51: Create and use a CustomResourceDefinition

Create a `CustomResourceDefinition` for a namespaced resource named `Widget` with these requirements:

- Group: `example.com`
- Version: `v1`
- Plural: `widgets`
- Singular: `widget`
- Kind: `Widget`
- Short name: `wd`
- Add one string field under `spec`, named `size`

Then create a custom resource named `sample-widget` with `spec.size=small`.

Save the manifests as `crd.yaml` and `widget.yaml`, then apply them.

