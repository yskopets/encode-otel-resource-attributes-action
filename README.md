## Usage

```yaml
steps:
  - id: otel-resource-attributes
    uses: yskopets/encode-otel-resource-attributes-action@v1
    with:
      attributes: |
        service.name=My Workflow
        service.version=${{ github.sha }}
        deployment.environment=prod

  - name: Use properly-encoded string
    env:
      OTEL_RESOURCE_ATTRIBUTES: ${{ steps.otel-resource-attributes.outputs.value }}
    run: |
      echo "OTEL_RESOURCE_ATTRIBUTES=${OTEL_RESOURCE_ATTRIBUTES}"
```