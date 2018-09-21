FROM aquintero446/opencv:pip3.4.3v2.09.19.2018
MAINTAINER "Andres Quintero"

WORKDIR /
RUN pip install pandas \
                sklearn \
                matplotlib \
                jupyter

RUN ["mkdir", "notebooks"]

# Recomended directory for store notebooks
VOLUME /notebooks

RUN jupyter notebook --generate-config --allow-root
RUN echo "c.NotebookApp.password = u'sha1:6a3f528eec40:6e896b6e4828f525a6e20e5411cd1c8075d68619'" >> /root/.jupyter/jupyter_notebook_config.py
EXPOSE 8888
CMD ["jupyter", "notebook", "--allow-root", "--notebook-dir=/notebooks", "--ip=0.0.0.0", "--port=8888", "--no-browser"]


#Command to run docker container
#docker run -it -p 8888:8888 -v $(pwd)/notebooks:/notebooks aquintero446/opencv-jupyter:v1.09.21.2018
# --Replace $(pwd) with your notebooks directory on your computer host, example: -v D:\cv-2018-2:/notebooks
#Acces on your browser http://localhost:8888/ and password root
