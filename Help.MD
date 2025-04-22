npm init -y ==> to create node backend server
npm i -D ts-node typescript @types/node ==> to install typescript dependency
npx tsc --init ==> for tsconfig.json
goto tsconfig.json => search module
modify module ==> to "nodenext"
then uncomment moduleResolution and modify to ==> "nodenext"
goto "resolveJsonModule" and uncomment and keep it true.
goto "outDir" and modify to "./dist"
now add an object ==> "include" : ["src/**/*", "src/data/**/*.json", "prisma/**/*"] ==> this will allow to include the typescript files

====================================================
npm i prisma @prisma/client
npx prisma init
now copy https://github.com/ed-roh/project-management/tree/f9aab0aa2de60d204f6aba5f2955288a592b4c83/server/prisma/seedData => paste seed data folder to prisma folder.

Now copy seed.ts file in prisma folder

Edit schema.prisma and add all models and relations

goto package.json => add "seed" : "ts-node prisma/seed.ts" in scripts. This will identify and seed the data we have
-------------------------Database Connection----------------
Now create .env in root directory and add => DATABASE_URL="postgresql://username:password@servername:port/dtabasename?schema=public"

Now npx prisma generate => to generate and connect prsima database
then ==> npx prisma migrate dev --name init ==> to load and migrate data
Now ==> npm run seed

-----------------------Other Backend depency-----------------
Now ==>npm i express body-parser cors dotenv helmet morgan

==>npm i -D rimraf concurrently nodemon @types/cors @types/express @types/morgan @types/node

Package | Purpose
rimraf | Like rm -rf, it deletes folders/files — handy for clean builds.
concurrently | Lets you run multiple npm scripts at once — e.g. server + watch.
nodemon | Auto-restarts your server on file changes — ideal for development.
@types/cors | Type definitions for cors middleware (used in Express apps).
@types/express | TypeScript types for Express.
@types/morgan | Types for morgan (HTTP logger middleware).
@types/node | Node.js types — required for any TypeScript backend.

---------------------------------------------------------
Now create index.ts under src directory in root directory
write code.
under scripts in package.json add =>
"build": "rimraf dist && npx tsc",
"start" : "npm run build && node dist/index.ts",
"dev" : "npm run build && concurrently \"npx tsc -w\" \"nodemon --exec ts-node src/index.ts\"",