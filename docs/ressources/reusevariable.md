3

Here is an example which reads metadata.name

          - name: POD_NAME
            valueFrom:
              fieldRef:
                fieldPath: metadata.name
          - name: LOG_FILE_NAME
            value: "/app/log/$(POD_NAME).log"
Here is another example, which reads metadata.namespace

          - name: POD_NAMESPACE
            valueFrom:
              fieldRef:
                fieldPath: metadata.namespace
          - name: REACT_APP_DB_URI
            value: "http://api-$(POD_NAMESPACE).org.com"
One more example, demonstrating how to read from metadata.labels

          - name: SRVC_NAME
            valueFrom:
              fieldRef:
                fieldPath: metadata.labels['app']
          - name: LOG_FILE_NAME
            value: '/app/log/$(SRVC_NAME).log'
