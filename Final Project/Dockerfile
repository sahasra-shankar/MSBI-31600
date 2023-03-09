FROM python:3.9.16

#ENV ES_FOLDER_NAME elasticsearch-7.8.0
ADD . /spapp
WORKDIR /spapp
RUN pip install -r requirements.txt
#CMD ["python", "app.py"]

CMD ["flask", "run", "--host=0.0.0.0","--port=8000"]