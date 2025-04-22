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