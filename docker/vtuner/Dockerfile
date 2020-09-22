# Create a fake vTuner service, since vTuner have started charing marantz users for theirs.

FROM python
RUN pip install ycast
CMD [ "python", "-m", "ycast", "-p", "${PORT:-8080}" ]