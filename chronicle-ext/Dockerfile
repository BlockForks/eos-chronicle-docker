FROM eostribe/chronicle
COPY entrypoint-ext.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/entrypoint-ext.sh
WORKDIR /opt/data

ENTRYPOINT ["/usr/bin/env"]
CMD ["bash", "/usr/local/bin/entrypoint-ext.sh"]

