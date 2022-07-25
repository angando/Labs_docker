FROM python:2.7-stretch
# --------------- FIN COUCHE OS ---------------------


# MÉTADONNÉES DE L'IMAGE
LABEL version="1.0" maintainer="NGANDO ARMEL <ngandoarmel@yahoo.fr>"


# VARIABLES TEMPORAIRES
ARG DOCUMENTROOT="/"


# --------------- DÉBUT FLASK ------------------
RUN apt-get update -y && \
apt install python3-pip -y && \
apt-get install python-dev python3-dev libsasl2-dev python-dev libldap2-dev libssl-dev -y && \
python -m pip install flask==1.1.2 flask_httpauth==4.1.0 flask_simpleldap python-dotenv==0.14.0


COPY student_age.py /

# --------------- FIN COUCHE FLASK --------------------


# OUVERTURE DU PORT DE L'API
EXPOSE 5000

# CREATION DU VOLUME PERSISTANT OU SERONT STOCKEES LES DATAS DE STUDENTS
VOLUME /data

#NE pas faire un copy des fichiers qui varient car il faudra refaire un build pour faire la mise à jour
#le mieux serait de démarrer l'application en mappant le fichier dans l'application
#exemple: docker run --name toto -v student_age.json:/data/student_age.json
# COPY DU FICHIER DES NOMS DE ETUDIANTS DANS LE POINT DE MONTAGE
#COPY  student_age.json /data/

# DÉMARRAGE DES SERVICES LORS DE L'EXÉCUTION DE L'IMAGE
CMD [ "python", "./student_age.py" ]

WORKDIR ${DOCUMENTROOT}
