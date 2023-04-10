# njs-request-response

This configuration for the NJS module on the NGINX+ Ingress Controller that will return the full request and response payloads for use with logging. In order to use the NJS module you will need to make sure it's enabled under main-snippets either in the controller.config.entries key in the values.yaml file or via your external configmap (making sure controller.customConfigMap is set in values.yaml) under the data key.

You also need to mount the js file with the request/response body retrieval functions as a volume into the nginx-ingress container. This can be done on the values.yaml file via the volumes and volumeMounts keys respectively. Finally, you need to make sure that the line js_body_filter rrb.getResponseBody; shows up under your location snippets in the Ingress resource. 
