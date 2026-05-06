FROM python:3.11

WORKDIR /app

# copy all files
COPY . .

# install dependencies
RUN pip install -r requirements.txt

# run backend
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]