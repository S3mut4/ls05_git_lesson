# ==============================================================================
# FLUJO DE TRABAJO CON BRANCHES EN GIT
# ==============================================================================

# 1. UPDATE YOUR BRANCH (Actualizar tu rama)
# Cambia a tu rama de trabajo
git checkout tu-rama

# Descarga las últimas novedades del servidor remoto sin aplicarlas aún
git fetch origin

# Integra los cambios más recientes de la rama principal (ej. main) en tu rama
git merge origin/main


# 2. CHANGE (Realizar cambios)
# Realiza la edición de archivos en tu editor/IDE preferido.
# Para revisar qué archivos has modificado o creado:
git status


# 3. TEST (Probar)
# Ejecuta la suite de pruebas o comandos de verificación de tu proyecto.
# Ejemplos (descomenta el que aplique a tu proyecto):
# npm test
# pytest
# cargo test


# 4. COMMIT (Confirmar cambios localmente)
# Prepara todos los archivos modificados para el commit
git add .

# Guarda el conjunto de cambios localmente con un mensaje claro y descriptivo
git commit -m "feat: descripción breve de los cambios realizados"


# 5. PUSH (Subir cambios al servidor remoto)
# Envía los commits de tu rama local hacia la rama remota correspondiente
git push origin tu-rama


# 6. PULL REQUEST (Crear solicitud de extracción)
# Si tienes instalada la herramienta GitHub CLI (gh):
gh pr create

# Nota: Si no usas GitHub CLI, ve a la interfaz web de GitHub/GitLab/Bitbucket
# y haz clic en el botón "Compare & pull request" que aparecerá en la página principal.


# ==============================================================================
# FLUJO COMPLETO EN BASH branch con multiples commits y PR
# ==============================================================================

# 1. CREATE A BRANCH (Crear una rama desde main)
# Asegúrate de estar en main y actualizado antes de derivar
git checkout main
git pull origin main
# Crea y cámbiate a la nueva rama de trabajo
git checkout -b feature/nueva-funcionalidad


# 2. DEVELOP, COMMIT AND PUSH (Desarrollar, hacer commits y subir)
# Realiza tus cambios y haz commits secuenciales (C1, C2, C3 en el diagrama)
git add .
git commit -m "C1: primer avance"

git add .
git commit -m "C2: segundo avance"

git add .
git commit -m "C3: funcionalidad terminada"

# Subes la rama con sus commits al remoto
git push origin feature/nueva-funcionalidad


# 3. GET CODE REVIEW (Revisión de código / Pull Request)
# Creas la Pull Request (PR) en GitHub/GitLab para ser revisada
gh pr create --title "feature: nueva funcionalidad" --body "Revisión de C1, C2 y C3"
# (Si no usas GitHub CLI, este paso se realiza en la página web)


# 4. MERGE TO DEFAULT BRANCH (Fusionar a la rama principal)
# Una vez aprobada la revisión, integras los cambios a main:
git checkout main
git pull origin main
git merge feature/nueva-funcionalidad
git push origin main

# (Opcional) Borrar la rama local y remota para mantener limpio el proyecto
git branch -d feature/nueva-funcionalidad
git push origin --delete feature/nueva-funcionalidad