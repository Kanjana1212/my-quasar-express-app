
<template>
  <q-page padding>
    <div class="text-h4 q-mb-md">
      Version Control + Docker Demo (Quasar)
    </div>

    <!-- Git Workflow -->
    <q-card class="q-mb-md">
      <q-card-section>
        <div class="text-h6">
          Git Workflow (ตัวอย่างขั้นตอนทำงาน)
        </div>

        <q-list bordered separator class="q-mt-sm">
          <q-item v-for="(step, index) in gitSteps" :key="index">
            <q-item-section avatar>
              <q-badge>{{ index + 1 }}</q-badge>
            </q-item-section>
            <q-item-section>
              <q-item-label>{{ step.title }}</q-item-label>
              <q-item-label caption>{{ step.detail }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-card-section>
    </q-card>

    <!-- Docker Concepts -->
    <q-card class="q-mb-md">
      <q-card-section>
        <div class="text-h6">Docker Concepts (สรุปสั้น ๆ)</div>

        <q-list bordered separator class="q-mt-sm">
          <q-item v-for="(item, index) in dockerItems" :key="index">
            <q-item-section>
              <q-item-label>{{ item.title }}</q-item-label>
              <q-item-label caption>{{ item.detail }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-card-section>
    </q-card>

    <!-- Docker Quick Reference -->
    <q-card>
      <q-card-section>
        <div class="text-h6">Docker Quick Reference</div>

        <q-list bordered separator class="q-mt-sm">
          <q-item v-for="(command, index) in dockerCommands" :key="index">
            <q-item-section>
              <q-item-label class="text-weight-bold">
                {{ command.name }}
              </q-item-label>
              <q-item-label caption>
                {{ command.detail }}
              </q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script setup>
const gitSteps = [
  {
    title: 'แก้โค้ด Quasar ใน src/',
    detail: 'เพิ่มหน้า / component ใหม่ เช่น IndexPage.vue, Layout ต่าง ๆ',
  },
  {
    title: 'ตรวจสอบสถานะไฟล์',
    detail: 'ใช้ git status ดูว่าไฟล์ไหนเปลี่ยนแปลงบ้าง',
  },
  {
    title: 'เพิ่มไฟล์เข้า staging',
    detail: 'ใช้ git add . หรือ git add src/pages/IndexPage.vue',
  },
  {
    title: 'สร้าง commit พร้อมข้อความแบบ Conventional Commits',
    detail: 'เช่น feat: add Git workflow demo page',
  },
  {
    title: 'push ขึ้น GitHub',
    detail: 'ใช้ git push origin feature/quasar-version-control-page แล้วเปิด Pull Request',
  },
]

const dockerItems = [
  {
    title: 'Image',
    detail: 'แม่พิมพ์ของ container สร้างจาก Dockerfile เช่น image สำหรับ Quasar SPA',
  },
  {
    title: 'Container',
    detail: 'instance ของ image ที่กำลังรัน เช่น container ที่รัน Nginx เสิร์ฟไฟล์ของ Quasar',
  },
  {
    title: 'Volume',
    detail: 'ใช้เก็บข้อมูลถาวร เช่น log / ไฟล์ upload',
  },
  {
    title: 'Network',
    detail: 'เชื่อม container ระหว่างกัน เช่น frontend คุยกับ backend ผ่าน network ของ Docker',
  },
]

const dockerCommands = [
  {
    name: 'docker build',
    detail: 'ใช้สร้าง Docker Image จาก Dockerfile เมื่อต้องการสร้างหรืออัปเดต Image',
  },
  {
    name: 'docker run',
    detail: 'ใช้สร้างและเริ่มต้น Container จาก Image เมื่อต้องการเปิดใช้งานแอป',
  },
  {
    name: 'docker ps',
    detail: 'ใช้ตรวจสอบ Container ที่กำลังทำงานอยู่',
  },
  {
    name: 'docker compose up -d --build',
    detail: 'ใช้ Build Image และเริ่มบริการทั้งหมดตามไฟล์ Compose ในโหมดเบื้องหลัง',
  },
  {
    name: 'docker compose down',
    detail: 'ใช้หยุดและลบ Container และ Network ที่สร้างโดย Docker Compose',
  },
]
</script>
