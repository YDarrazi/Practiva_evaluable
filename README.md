
# 1. Creación de la carpeta practica_evaluable y su conversión a un repositorio Git.
mkdir practica_evaluable
cd practica_evaluable
git init

# 2. Creación de dos archivos documento1.txt y documento2.txt, añadiendo texto en ambos y validándolos en el repositorio local.
echo "Texto para documento 1" > documento1.txt
echo "Texto para documento 2" > documento2.txt
git add documento1.txt documento2.txt
git commit -m "Añadir documento1 y documento2"

# 3. Realización de más cambios en el primer documento, añadiendo líneas, y validándolo.
echo "Nueva línea para documento 1" >> documento1.txt
git commit -am "Actualizar documento1"

# 4. Realización de cambios en el segundo documento y validación.
echo "Nueva línea para documento 2" >> documento2.txt
git commit -am "Actualizar documento2"

# 5. Reversión a la situación antes de los cambios en el segundo documento.
git reset HEAD~1

# 6. Creación del archivo documento3.txt, añadiendo cambios y validándolo.
echo "Texto para documento 3" > documento3.txt
git add documento3.txt
git commit -m "Añadir documento3"

# 7. Reversión del último commit.
git reset HEAD~1

# 8. Conexión a un repositorio remoto público en GitHub con nombre practica_evaluable y subida de la información del repositorio local.
git remote add origin (https://github.com/YDarrazi/Practiva_evaluable)
git push -u origin main

# 9. Creación de una rama llamada mirama. En ella se añaden dos archivos, rama1.txt y rama2.txt, se modifican con varias líneas y se validan.
git checkout -b mirama
echo "Texto para rama 1" > rama1.txt
echo "Texto para rama 2" > rama2.txt
git add rama1.txt rama2.txt
git commit -m "Añadir rama1 y rama2"

# 10. Fusión de la rama mirama con la rama main. Borrado de la rama mirama.
git checkout main
git merge mirama
git branch -d mirama

# 11. Sincronización de los cambios con el repositorio remoto.
git push origin main

# 12. Creación de una etiqueta con V1 y subida de la etiqueta al remoto.
git tag V1
git push origin V1

# 13. Clonado del repositorio remoto practica_evaluable a un nuevo directorio en disco local llamado practica_evaluable_2.
cd ..
git clone (https://github.com/YDarrazi/Practiva_evaluable) practica_evaluable_2

# 14. Creación de una rama llamada mirama y en ella se realizan cambios en el documento1.txt, se valida y se sube al repositorio remoto.
cd practica_evaluable_2
git checkout -b mirama
echo "Texto adicional para documento 1" >> documento1.txt
git commit -am "Actualizar documento1 en rama mirama"
git push origin mirama

# 15. Realización de cambios en la rama main del documento2.txt. Se validan y se suben al repositorio.
git checkout main
echo "Texto adicional para documento 2" >> documento2.txt
git commit -am "Actualizar documento2 en rama main"
git push origin main

# 16. Realización de un merge entre las dos ramas. Borrado de la rama mirama.
git merge mirama
git branch -d mirama
git push origin main

# 17. Realización de cambios en el documento2.txt.
echo "Más texto para documento 2" >> documento2.txt
git commit -am "Actualizar documento2"

# 18. Creación de una rama llamada mirama y en esta se realizan cambios distintos en el documento2.txt, que los realizados en la rama main, en el punto anterior.
git checkout -b mirama
echo "Texto diferente para documento 2" >> documento2.txt
git commit -am "Actualizar documento2 en rama mirama"

# 19. Fusión de los cambios de las dos ramas. Resolución del conflicto.
git checkout main
git merge mirama
# En este punto, se abrirá un editor para resolver el conflicto en documento2.txt
git commit -am "Resolver conflicto en documento2"

# 20. Sincronización con el repositorio remoto.
git push origin main

# 21. Añadir a tu repositorio remoto un archivo README.md. En el añade una breve descripción del ejercicio que acabas de realizar. Añade los comandos Git empleados durante la tarea.
echo "# Práctica Evaluable\n\nEste repositorio contiene la práctica evaluable de Git." > README.md
git add README.md
git commit -m "Añadir README"
git push origin main

# 22. Llevar los cambios al repositorio local. Sincronizarlos.
git pull origin main
