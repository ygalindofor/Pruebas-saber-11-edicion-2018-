{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "W-Dxk9NJ0jgQ"
   },
   "source": [
    "#Analisis de los resultados de las pruebas saber 11 edicion 2018 a traves de tecnicas de mineria de datos"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "rcsokugu1Cbj"
   },
   "source": [
    "####primero se importan las librerias necesarias"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "fYM8l5h4HA-7"
   },
   "source": [
    "### import libs"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "grSJUONQKI_H"
   },
   "outputs": [],
   "source": [
    "import pandas as pd"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "4BHtUTvb1ogq"
   },
   "source": [
    "####Luego para la lectura del dataset a traves de la libreria pandas como pd lo podemos leer, ya que en este caso es un .csv se lee con pd.read_csv\n",
    "####Fuera un .json o otro tipo de dataset la sintaxis no es que cambie mucho "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "4IjBs2-t2WcR"
   },
   "source": [
    "####json       pd.read_json()\n",
    "####excel      pd.read_excel()\n",
    "####sql        pd.read_sql()\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "v46I9DQi3hjk"
   },
   "source": [
    "####hay que tener encuenta con que caracter estan separados los datos en este caso es con , y por ello se añade la sintaxis sep=','"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "EP87LmRd43y8"
   },
   "source": [
    "####low_memory=False    Es un parametro que funciona para la limpieza de los datos"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "-M2tjtOaKbx_"
   },
   "outputs": [],
   "source": [
    "url = 'Saber_11__2018-2.csv'\n",
    "pruebasSaber11_df = pd.read_csv(url, sep=',', low_memory=False)\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 935
    },
    "colab_type": "code",
    "id": "vWJ-DNgRPL_E",
    "outputId": "af921997-98bc-443d-ae24-e22e6cf8f9fd"
   },
   "outputs": [],
   "source": [
    "pruebasSaber11_df.head(10)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 359
    },
    "colab_type": "code",
    "id": "IwMvKcVPQztg",
    "outputId": "3a43415d-a5a6-4b61-c781-30e1fa405f93"
   },
   "outputs": [],
   "source": [
    "pruebasSaber11_df = pruebasSaber11_df.iloc[:, [13,16, 22, 24, 64]]\n",
    "pruebasSaber11_df.head(10)"
   ]
  }
 ],
 "metadata": {
  "colab": {
   "name": "pruebassaber11.ipynb",
   "provenance": [],
   "toc_visible": true
  },
  "kernelspec": {
   "display_name": "Python 3",
   "name": "python3"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 0
}
