<template>
  <div class="intro-wrapper">
    <div class="background-container">
      <div class="background-image"></div>
    </div>

    <div class="showcase-page" ref="pageContainerRef">
      <section class="scroll-section hero">
        <div class="content">
          <h1 class="hero-title">幻语次原</h1>
          <p class="hero-subtitle">与你最爱的角色，开启一场真实的沉浸式对话</p>
        </div>
      </section>

      <section class="scroll-section team-interactive">
        <div class="content">
          <h2>团队成员介绍</h2>
          <transition-group name="member-fade" tag="div" class="members-container-interactive">
            <div
              v-for="member in visibleMembers" :key="member.id"
              class="member-card"
              :class="{ active: selectedMemberId === member.id }"
              @click="selectMember(member.id)"
            >
              <div class="member-initial-view">
                <div class="member-photo-interactive">
                  <img :src="member.photo" :alt="member.name" />
                </div>
                <div class="member-info-interactive">
                  <h3>{{ member.name }}</h3>
                  <p class="member-role-interactive">{{ member.role }}</p>
                </div>
              </div>

              <transition name="details-fade">
                <div v-if="selectedMemberId === member.id" class="member-details">
                  <h4>核心贡献</h4>
                  <ul>
                    <li v-for="(item, index) in member.contributions" :key="index">{{ item }}</li>
                  </ul>
                </div>
              </transition>
            </div>
          </transition-group>
        </div>
      </section>

      <section class="scroll-section design-philosophy">
        <div class="content">
          <h2>设计思路介绍</h2>
          <transition-group name="philosophy-fade" tag="div" class="philosophy-grid-interactive">
            <div
              v-for="item in visiblePhilosophyItems"
              :key="item.id"
              class="philosophy-card-interactive"
              :class="{ active: selectedPhilosophyId === item.id }"
              @click="selectPhilosophy(item.id)"
            >
              <div class="philosophy-initial-view">
                <div class="philosophy-icon">{{ item.icon }}</div>
                <h3>{{ item.title }}</h3>
              </div>

              <transition name="philosophy-details-fade">
                <div v-if="selectedPhilosophyId === item.id" class="philosophy-details">
                  <div v-html="item.content"></div>
                </div>
              </transition>
            </div>
          </transition-group>
        </div>
      </section>

      <section class="scroll-section design-process">
        <div class="content">
          <h2>产品设计流程思路</h2>
          <div class="process-sections">
            <div class="process-item">
              <h3>🎙️ 实时语音对话完整流程设计</h3>
              <div class="flow-description">
                <p>我们设计了一套完整的实时语音对话系统，从用户语音输入到AI语音回复，整个流程实现了毫秒级的响应速度和高质量的交互体验。</p>
              </div>
              <div class="flow-diagram">
                <div class="flow-step">
                  <div class="step-number">1</div>
                  <div class="step-content">
                    <h4>🎤 音频采集</h4>
                    <p>Web Audio API捕获麦克风</p>
                    <p class="tech-detail">16kHz PCM格式</p>
                  </div>
                </div>
                <div class="flow-arrow">→</div>
                <div class="flow-step">
                  <div class="step-number">2</div>
                  <div class="step-content">
                    <h4>📡 实时传输</h4>
                    <p>WebSocket流式上传音频</p>
                    <p class="tech-detail">分段传输，低延迟</p>
                  </div>
                </div>
                <div class="flow-arrow">→</div>
                <div class="flow-step">
                  <div class="step-number">3</div>
                  <div class="step-content">
                    <h4>🔍 语音识别</h4>
                    <p>阿里云ASR实时转录</p>
                    <p class="tech-detail">智能断句与去重</p>
                  </div>
                </div>
                <div class="flow-arrow">→</div>
                <div class="flow-step">
                  <div class="step-number">4</div>
                  <div class="step-content">
                    <h4>🧠 AI推理</h4>
                    <p>千问Plus模型生成回复</p>
                    <p class="tech-detail">角色化Prompt + 记忆管理</p>
                  </div>
                </div>
                <div class="flow-arrow">→</div>
                <div class="flow-step">
                  <div class="step-number">5</div>
                  <div class="step-content">
                    <h4>🎵 语音合成</h4>
                    <p>GPT-SoVITS角色声线</p>
                    <p class="tech-detail">TTS服务</p>
                  </div>
                </div>
                <div class="flow-arrow">→</div>
                <div class="flow-step">
                  <div class="step-number">6</div>
                  <div class="step-content">
                    <h4>🔊 流式播放</h4>
                    <p>前端实时音频播放</p>
                    <p class="tech-detail">支持打断与队列管理</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section class="scroll-section project-highlights">
        <div class="content">
          <h2>项目亮点展示</h2>
          <div class="highlights-container">
            <div class="highlight-category fronted">
              <h3>前端Vue核心亮点</h3>
              <div class="highlight-items">
                <div class="highlight-item">
                  <h4>🎙️ 实时音频处理</h4>
                  <p>基于Web Audio API和Recorder-core库实现高质量音频录制，支持PCM格式16kHz采样率，确保语音识别准确性</p>
                </div>
                <div class="highlight-item">
                  <h4>🔄 WebSocket双向通信</h4>
                  <p>实现音频数据的实时双向传输，支持语音上行和TTS音频下行的流式处理，提供低延迟的交互体验</p>
                </div>
                <div class="highlight-item">
                  <h4>🎭 多角色动态切换</h4>
                  <p>支持宵宫、温迪、胡桃三个角色的无缝切换，每个角色拥有独立的对话历史和个性化设定</p>
                </div>
                <div class="highlight-item">
                  <h4>🎵 流式音频播放</h4>
                  <p>实现TTS音频的流式接收与播放，支持音频打断、队列管理和播放状态控制</p>
                </div>
                <div class="highlight-item">
                  <h4>📱 响应式设计</h4>
                  <p>采用现代CSS技术实现完全响应式界面，支持桌面端和移动端的优秀体验</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section class="scroll-section project-highlights">
        <div class="content">
          <h2>项目亮点展示</h2>
          <div class="highlight-category backend">
            <h3>后端Java核心亮点</h3>
            <div class="highlight-items">
              <div class="highlight-item">
                <h4>🎯 原型作用域WebSocket处理器</h4>
                <p>WebSocketSpeechTranscriber采用@Scope("prototype")设计，为每个会话创建独立实例，确保线程安全</p>
              </div>
              <div class="highlight-item">
                <h4>🧠 智能对话记忆管理</h4>
                <p>MyChatMemoryStore实现本地文件缓存优化，避免重复存储SYSTEM消息，提升响应速度和存储效率</p>
              </div>
              <div class="highlight-item">
                <h4>🔄 流式AI对话处理</h4>
                <p>基于Reactor响应式编程，实现AI文本的流式生成和实时推送，提供更自然的对话体验</p>
              </div>
              <div class="highlight-item">
                <h4>🎤 实时语音转录</h4>
                <p>集成阿里云ASR服务，支持实时音频流处理、智能断句和去重机制，确保识别准确性</p>
              </div>
              <div class="highlight-item">
                <h4>🔊 多端口TTS服务</h4>
                <p>MessageTurnToAiVoiceTool支持多角色TTS服务的动态端口分配，实现角色声音的个性化</p>
              </div>
              <div class="highlight-item">
                <h4>⚡ 异步音频处理</h4>
                <p>采用ExecutorService实现音频播放的串行处理，避免并发交错，支持音频打断和队列管理</p>
              </div>
              <div class="highlight-item">
                <h4>🛡️ 健壮的错误处理</h4>
                <p>完善的异常处理机制，支持重试策略、超时控制和优雅降级，确保服务稳定性</p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section class="scroll-section final-results">
        <div class="content">
          <h1 class="large-title">最终结果展示</h1>
          <p class="large-subtitle">现场演示即将开始</p>
          <div class="demo-info">
            <h2>演示内容</h2>
            <ul class="demo-list">
              <li>实时语音识别与AI对话</li>
              <li>多角色语音合成效果</li>
              <li>WebSocket实时通信</li>
              <li>完整的用户交互流程</li>
            </ul>
          </div>
        </div>
      </section>

      <section class="scroll-section tech-stack">
        <div class="content">
          <h2>技术架构</h2>
          <div class="tech-grid">
            <div class="tech-item">
              <h3>前端技术</h3>
              <p>Vue 3 + TypeScript</p>
              <p>WebSocket实时通信</p>
              <p>Web Audio API</p>
            </div>
            <div class="tech-item">
              <h3>后端技术</h3>
              <p>Spring Boot</p>
              <p>LangChain4j</p>
              <p>阿里云ASR</p>
            </div>
            <div class="tech-item">
              <h3>AI模型</h3>
              <p>千问Plus LLM</p>
              <p>GPT-SoVITS TTS</p>
              <p>实时语音合成</p>
            </div>
          </div>
        </div>
      </section>
    </div>

    <div class="scroll-indicator">
      <div
        v-for="index in totalSections"
        :key="index"
        class="scroll-dot"
        :class="{ active: currentSectionIndex === index - 1 }"
        @click="scrollToSection(index - 1)"
      ></div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, onUnmounted, ref, computed } from 'vue';

const pageContainerRef = ref<HTMLElement | null>(null);

const mainAppUrl = ref('http://localhost:5173/login');
const members = ref([
  { id: 'jzc', name: '江在程', photo: '/江在程_简历照.jpg', role: 'Java后端 / TTS', contributions: ['用户认证与会话管理', '对象存储与文件服务', 'LangChain4j集成与提示词工程', 'GPT-SoVITS语音合成接口封装','部分前端接口连接代码'] },
  { id: 'lwj', name: '李文杰', photo: '/李文杰_简历照.jpg', role: 'Java后端 / 语音处理', contributions: ['阿里云ASR服务集成与SDK重构', '用户信息管理模块', '数据库存储优化与数据校验','AI模型调度与结果转发'] },
  { id: 'lzy', name: '刘镇源', photo: '/刘镇源_简历照.jpg', role: '前端开发工程师', contributions: ['Vue3 + TS 前端架构设计', 'WebSocket实时通信与音频处理', '用户认证与个人中心全流程开发', '双模式聊天界面设计与实现', '整体应用的UI/UX打磨与交互优化'] }
]);
const selectedMemberId = ref<string | null>(null);
const selectMember = (id: string | null) => {
  selectedMemberId.value = selectedMemberId.value === id ? null : id;
};
const visibleMembers = computed(() => {
  if (!selectedMemberId.value) return members.value;
  return members.value.filter(member => member.id === selectedMemberId.value);
});

// 设计思路数据
const philosophyItems = ref([
  {
    id: 'philosophy-1',
    icon: '🎯',
    title: '目标用户与痛点分析',
    content: `
      <p><strong>目标用户：</strong>原神游戏爱好者、二次元文化爱好者、AI技术体验者</p>
      <p><strong>用户痛点：</strong></p>
      <ul>
        <li>传统文字聊天缺乏沉浸感，无法体验角色真实的声音</li>
        <li>现有AI助手缺乏个性化角色设定，对话体验单调</li>
        <li>语音交互门槛高，需要复杂的技术配置</li>
      </ul>
      <p><strong>用户故事：</strong>作为一名原神玩家，我希望能够与游戏中的角色进行真实的语音对话，感受角色的个性和魅力，获得更加沉浸式的互动体验。</p>
    `
  },
  {
    id: 'philosophy-2',
    icon: '⚡',
    title: '功能需求与优先级',
    content: `
      <p><strong>核心功能（高优先级）：</strong></p>
      <ul>
        <li>实时语音识别与转文字 ✅ 已开发</li>
        <li>AI角色对话生成 ✅ 已开发</li>
        <li>语音合成与播放 ✅ 已开发</li>
      </ul>
      <p><strong>增强功能（中优先级）：</strong></p>
      <ul>
        <li>多角色切换 ✅ 已开发（宵宫、温迪、胡桃）</li>
        <li>对话历史记录 ✅ 已开发</li>
        <li>WebSocket实时通信 ✅ 已开发</li>
      </ul>
      <p><strong>扩展功能（低优先级）：</strong></p>
      <ul>
        <li>情感识别与表达（暂未实现）</li>
        <li>多语言支持（暂未实现）</li>
      </ul>
    `
  },
  {
    id: 'philosophy-3',
    icon: '🤖',
    title: 'LLM模型选择与对比',
    content: `
      <p><strong>当前采用：</strong>千问Plus模型</p>
      <p><strong>选择理由：</strong></p>
      <ul>
        <li><strong>中文优化：</strong>千问Plus在中文理解和生成方面表现优异</li>
        <li><strong>角色扮演：</strong>支持复杂的角色设定和个性化对话</li>
        <li><strong>响应速度：</strong>流式输出，实时性好</li>
      </ul>
      <p><strong>对比分析：</strong></p>
      <ul>
        <li>vs GPT-4：千问Plus在中文场景下更适合，成本更低</li>
        <li>vs Claude：千问Plus在角色扮演方面更灵活</li>
        <li>vs 文心一言：千问Plus的API稳定性和文档完善度更好</li>
      </ul>
    `
  },
  {
    id: 'philosophy-4',
    icon: '✨',
    title: 'AI角色技能期望',
    content: `
      <p><strong>除语音聊天外的期望技能：</strong></p>
      <ul>
        <li><strong>情感理解：</strong>识别用户情绪状态，给出相应的安慰或鼓励</li>
        <li><strong>知识问答：</strong>回答原神游戏相关的问题和攻略</li>
        <li><strong>角色一致性：</strong>保持角色设定的连贯性和个性特征</li>
        <li><strong>多轮对话：</strong>维持长期对话记忆，建立深度交互关系</li>
        <li><strong>创意生成：</strong>根据用户需求创作故事、诗歌等内容</li>
        <li><strong>个性化推荐：</strong>基于用户喜好推荐游戏内容或活动</li>
      </ul>
    `
  }
]);

const selectedPhilosophyId = ref<string | null>(null);
const selectPhilosophy = (id: string | null) => {
  selectedPhilosophyId.value = selectedPhilosophyId.value === id ? null : id;
};
const visiblePhilosophyItems = computed(() => {
  if (!selectedPhilosophyId.value) return philosophyItems.value;
  return philosophyItems.value.filter(item => item.id === selectedPhilosophyId.value);
});

const totalSections = ref(0);
const currentSectionIndex = ref(0);
let observer: IntersectionObserver | null = null;

const scrollToSection = (index: number) => {
  if (!pageContainerRef.value) return;
  const sections = pageContainerRef.value.querySelectorAll('.scroll-section');
  if (sections[index]) {
    sections[index].scrollIntoView({ behavior: 'smooth' });
  }
};

onMounted(() => {
  if (!pageContainerRef.value) return;

  const sectionsNodeList = pageContainerRef.value.querySelectorAll('.scroll-section');
  totalSections.value = sectionsNodeList.length;

  const options = {
    root: pageContainerRef.value,
    threshold: 0.7, // 当section的70%进入视口时，触发回调
  };

  const callback: IntersectionObserverCallback = (entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        // 将NodeList转换为数组以使用indexOf
        const sectionsArray = Array.from(sectionsNodeList);
        const index = sectionsArray.indexOf(entry.target as HTMLElement);
        if (index > -1) {
          currentSectionIndex.value = index;
        }
      }
    });
  };

  observer = new IntersectionObserver(callback, options);

  sectionsNodeList.forEach(section => {
    observer?.observe(section);
  });
});

onUnmounted(() => {
  if (observer) {
    observer.disconnect();
  }
});

</script>

<style scoped>
@use "sass:math";

:global(body) {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}

.intro-wrapper {
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}

.background-container {
  position: absolute;
  inset: 0;
  z-index: 1;
}

.background-image {
  width: 100%;
  height: 100%;
  background-image: url('/background1.jpg');
  background-size: cover;
  background-position: center;
  filter: blur(15px) brightness(0.4);
  transform: scale(1.1);
}

.showcase-page {
  position: absolute;
  inset: 0;
  z-index: 2;
  height: 100vh;
  overflow-x: hidden;
  overflow-y: scroll;
  scroll-snap-type: y mandatory;
  background-color: transparent;
}

.showcase-page::-webkit-scrollbar { display: none; }
.showcase-page { -ms-overflow-style: none; scrollbar-width: none; }

.scroll-section {
  height: 100vh;
  width: 100%;
  scroll-snap-align: start;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 40px;
  box-sizing: border-box;
  color: #e6edf3;
}

.scroll-indicator {
  position: absolute;
  right: 30px;
  top: 50%;
  transform: translateY(-50%);
  z-index: 3;
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.scroll-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.3);
  cursor: pointer;
  transition: all 0.4s;
}

.scroll-dot.active {
  background: #ffffff;
  box-shadow: 0 0 15px rgba(255, 255, 255, 0.7);
  transform: scale(1.4);
}


.scroll-dot:hover {
  background: rgba(255, 255, 255, 0.6);
  transform: scale(1.1);
}

.hero {
  text-align: center;
}

.hero h1.hero-title {
  font-size: 7rem;
  font-weight: 700;
  letter-spacing: -1px;
  background: linear-gradient(135deg, #79c0ff, #c2e9fb);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-shadow: 0 0 20px rgba(121, 192, 255, 0.5), 0 0 40px rgba(121, 192, 255, 0.3);
  animation: title-breathe 5s ease-in-out infinite;
}

@keyframes title-breathe {
  0%, 100% {
    transform: scale(1);
    text-shadow: 0 0 20px rgba(121, 192, 255, 0.5), 0 0 40px rgba(121, 192, 255, 0.3);
  }
  50% {
    transform: scale(1.03);
    text-shadow: 0 0 30px rgba(121, 192, 255, 0.7), 0 0 60px rgba(121, 192, 255, 0.5);
  }
}

.hero p.hero-subtitle {
  font-size: 1.6rem;
  max-width: 650px;
  margin: 25px auto 40px;
  color: #c9d1d9;
  line-height: 1.7;
}

.tech-stack {
  text-align: center;
}

.tech-stack h2 {
  font-size: 3.5rem;
  font-weight: 700;
  margin-bottom: 40px;
}

.tech-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
  margin-top: 40px;
  max-width: 900px;
}
.tech-item {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 15px;
  padding: 25px 30px;
  text-align: center;
  transition: all 0.3s ease;
  flex: 1;
  min-width: 250px;
}
.tech-item:hover {
  transform: translateY(-5px);
  background: rgba(255, 255, 255, 0.08);
  border-color: rgba(56, 182, 255, 0.5);
}
.tech-item h3 {
  font-size: 1.5rem;
  color: #38b6ff;
  margin-bottom: 15px;
}
.tech-item p {
  font-size: 1.1rem;
  color: #c9d1d9;
  line-height: 1.6;
  margin: 5px 0;
}

.team-interactive h2 {
  font-size: 3.5rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 60px;
  color: #ffffff;
}

.members-container-interactive {
  display: flex;
  justify-content: center;
  gap: 40px;
  perspective: 1000px;
}

.member-card {
  width: 300px;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 20px;
  padding: 30px 20px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  text-align: center;
  cursor: pointer;
  transition: all 0.5s cubic-bezier(0.25, 0.8, 0.25, 1);
}

.member-card:hover:not(.active) {
  transform: translateY(-10px);
  border-color: rgba(0, 123, 255, 0.3);
}

.member-photo-interactive {
  width: 150px;
  height: 150px;
  margin: 0 auto 20px;
  border-radius: 50%;
  overflow: hidden;
  border: 3px solid rgba(255, 255, 255, 0.1);
}
.member-photo-interactive img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.member-info-interactive h3 {
  font-size: 1.8rem;
  margin-bottom: 8px;
}
.member-role-interactive {
  font-size: 1.1rem;
  color: #3DBBFF;
  font-weight: bold;
}

.member-card.active {
  width: 900px;
  min-height: 400px;
  background: rgba(30, 30, 45, 0.7);
  backdrop-filter: blur(10px);
  border-color: rgba(0, 123, 255, 0.4);
  cursor: default;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-start;
  gap: 40px;
  padding: 40px;
  position: relative;
}

.member-card.active .member-initial-view {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 15px;
  width: 250px;
  flex-shrink: 0;
  padding-right: 30px;
  border-right: 1px solid rgba(255, 255, 255, 0.1);
}

.member-details {
  margin-top: 0;
  text-align: left;
  border-top: none;
  padding-top: 0;
  flex-grow: 1;
}

.member-details h4 {
  font-size: 1.5rem;
  margin-bottom: 20px;
  color: #0ea5e9;
}

.member-details ul {
  list-style: none;
  padding: 0;
}

.member-details li {
  font-size: 20px;
  color: #c9d1d9;
  margin-bottom: 10px;
  padding-left: 25px;
  position: relative;
  line-height: 1.5;
}

.member-details li::before {
  content: '▸';
  position: absolute;
  left: 0;
  color: #3DBBFF;
  font-size: 1.2rem;
  top: 0px;
}

.member-fade-leave-active {
  transition: opacity 0.4s, transform 0.4s;
  position: absolute;
}

.member-fade-leave-to {
  opacity: 0;
  transform: scale(0.8);
}

.details-fade-enter-active, .details-fade-leave-active {
  transition: none;
}

.details-fade-enter-from, .details-fade-leave-to {
  opacity: 0;
}

.design-philosophy h2 {
  font-size: 3.5rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 60px;
  color: #ffffff;
}

.philosophy-grid-interactive {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 30px;
  max-width: 1000px;
  margin: 0 auto;
  perspective: 1000px;
}

.philosophy-card-interactive {
  background: rgba(255, 255, 255, 0.05);
  border-radius: 20px;
  padding: 30px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  cursor: pointer;
  transition: all 0.5s cubic-bezier(0.25, 0.8, 0.25, 1);
  min-height: 150px;
  display: flex;
  flex-direction: column;
}

.philosophy-card-interactive:hover:not(.active) {
  transform: translateY(-10px);
  border-color: rgba(0, 123, 255, 0.3);
  background: rgba(255, 255, 255, 0.08);
}

.philosophy-initial-view {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 15px;
}

.philosophy-icon {
  font-size: 3.5rem;
  filter: drop-shadow(0 0 20px rgba(0, 123, 255, 0.5));
  animation: icon-float 3s ease-in-out infinite;
}

@keyframes icon-float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
}

.philosophy-initial-view h3 {
  font-size: 1.5rem;
  font-weight: 600;
  color: #ffffff;
  margin: 0;
}

.philosophy-card-interactive.active {
  grid-column: 1 / -1;
  background: rgba(30, 30, 45, 0.7);
  backdrop-filter: blur(10px);
  border-color: rgba(0, 123, 255, 0.4);
  cursor: default;
  min-height: auto;
}

.philosophy-card-interactive.active .philosophy-initial-view {
  flex-direction: row;
  justify-content: flex-start;
  padding-bottom: 20px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  margin-bottom: 20px;
}

.philosophy-card-interactive.active .philosophy-icon {
  font-size: 2.5rem;
  animation: none;
}

.philosophy-card-interactive.active .philosophy-initial-view h3 {
  font-size: 1.8rem;
  color: #3DBBFF;
  text-align: left;
}

.philosophy-details {
  text-align: left;
  padding-top: 10px;
}

.philosophy-details :deep(p) {
  font-size: 20px;
  line-height: 1.7;
  margin-bottom: 15px;
  color: #e0e0e0;
}

.philosophy-details :deep(strong) {
  color: #ffffff;
  font-weight: 600;
  font-size: 24px;
}

.philosophy-details ul {
  list-style: none;
  padding: 0;
  margin: 10px 0 20px 0;
}

.philosophy-details :deep(li) {
  font-size: 20px;
  line-height: 1.6;
  margin-bottom: 10px;
  color: #c9d1d9;
  position: relative;
  padding-left: 25px;
}

.philosophy-details li::before {
  content: '▸';
  position: absolute;
  left: 0;
  color: #3DBBFF;
  font-size: 1.2rem;
  font-weight: bold;
}

.philosophy-fade-leave-active {
  transition: opacity 0.4s, transform 0.4s;
  position: absolute;
}

.philosophy-fade-leave-to {
  opacity: 0;
  transform: scale(0.9);
}

.philosophy-details-fade-enter-active, .philosophy-details-fade-leave-active {
  transition: none;
}

.philosophy-details-fade-enter-from, .philosophy-details-fade-leave-to {
  opacity: 0;
}

.design-process h2 {
  font-size: 3.5rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 40px;
  color: #ffffff;
  -webkit-background-clip: text;
  background-clip: text;
}

.process-sections {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 20px;
}

.process-item {
  background: rgba(255, 255, 255, 0.05);
  border-radius: 20px;
  padding: 40px;
  margin-bottom: 40px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.process-item:hover {
  background: rgba(255, 255, 255, 0.08);
  border-color: rgba(0, 123, 255, 0.3);
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 123, 255, 0.2);
}

.process-item h3 {
  font-size: 2rem;
  font-weight: 600;
  color: #3DBBFF;
  margin-bottom: 20px;
  text-align: center;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
}

.flow-description {
  text-align: center;
  margin-bottom: 30px;
}

.flow-description p {
  font-size: 1.1rem;
  line-height: 1.6;
  color: #e0e0e0;
  max-width: 800px;
  margin: 0 auto;
}

.flow-diagram {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 15px;
  margin: 30px 0;
  padding: 20px;
  background: rgba(0, 0, 0, 0.2);
  border-radius: 15px;
}

.flow-step {
  background: linear-gradient(135deg, rgba(0, 123, 255, 0.1), rgba(0, 123, 255, 0.05));
  border: 2px solid rgba(0, 123, 255, 0.3);
  border-radius: 15px;
  padding: 20px;
  text-align: center;
  min-width: 180px;
  transition: all 0.3s ease;
  backdrop-filter: blur(5px);
}

.flow-step:hover {
  background: linear-gradient(135deg, rgba(0, 123, 255, 0.2), rgba(0, 123, 255, 0.1));
  border-color: rgba(0, 123, 255, 0.5);
  transform: translateY(-3px) scale(1.02);
  box-shadow: 0 8px 25px rgba(0, 123, 255, 0.3);
}

.step-number {
  background: linear-gradient(135deg, #3DBBFF, #0056b3);
  color: white;
  width: 35px;
  height: 35px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  margin: 0 auto 10px;
  font-size: 1.1rem;
  box-shadow: 0 4px 15px rgba(0, 123, 255, 0.4);
}

.step-content h4 {
  font-size: 1.1rem;
  color: #ffffff;
  margin-bottom: 8px;
  font-weight: 600;
}

.step-content p {
  font-size: 0.9rem;
  color: #c9d1d9;
  margin-bottom: 5px;
  line-height: 1.4;
}

.tech-detail {
  font-size: 0.8rem !important;
  color: #8b949e !important;
  font-style: italic;
  background: rgba(0, 123, 255, 0.1);
  padding: 2px 8px;
  border-radius: 10px;
  display: inline-block;
}

.flow-arrow {
  font-size: 1.8rem;
  color: #3DBBFF;
  font-weight: bold;
  text-shadow: 0 2px 4px rgba(0, 123, 255, 0.5);
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.6; }
}

.project-highlights h2 {
  font-size: 3.5rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 50px;
  color: #ffffff;
  -webkit-background-clip: text;
  background-clip: text;
  text-shadow: 0 4px 8px rgba(0, 123, 255, 0.3);
}

.highlights-container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 20px;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(600px, 1fr));
  gap: 40px;
}

.highlight-category {
  background: rgba(255, 255, 255, 0.05);
  border-radius: 20px;
  padding: 35px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
  position: relative;
  overflow: hidden;
}

.highlight-category::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, #3DBBFF, #0056b3, #3DBBFF);
  background-size: 200% 100%;
  animation: shimmer 3s ease-in-out infinite;
}

@keyframes shimmer {
  0%, 100% { background-position: 200% 0; }
  50% { background-position: -200% 0; }
}

.highlight-category:hover {
  background: rgba(255, 255, 255, 0.08);
  border-color: rgba(0, 123, 255, 0.3);
  transform: translateY(-8px);
  box-shadow: 0 15px 40px rgba(0, 123, 255, 0.2);
}

.highlight-category h3 {
  font-size: 2.2rem;
  font-weight: 600;
  color: #3DBBFF;
  margin-bottom: 25px;
  text-align: center;
  position: relative;
  padding-bottom: 15px;
}

.highlight-category h3::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 3px;
  background: linear-gradient(90deg, #3DBBFF, #0056b3);
  border-radius: 2px;
}

.highlight-items {
  display: grid;
  gap: 20px;
  grid-template-columns: repeat(2, 1fr);
}

.highlight-item {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 15px;
  padding: 25px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.highlight-item::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 4px;
  height: 100%;
  background: linear-gradient(180deg, #3DBBFF, #0056b3);
  transform: scaleY(0);
  transform-origin: bottom;
  transition: transform 0.3s ease;
}

.highlight-item:hover::before {
  transform: scaleY(1);
  transform-origin: top;
}

.highlight-item:hover {
  background: rgba(255, 255, 255, 0.06);
  border-color: rgba(0, 123, 255, 0.2);
  transform: translateX(8px);
  box-shadow: 0 8px 25px rgba(0, 123, 255, 0.15);
}

.highlight-item h4 {
  font-size: 1.3rem;
  font-weight: 600;
  color: #ffffff;
  margin-bottom: 12px;
  display: flex;
  align-items: center;
  gap: 10px;
}

.highlight-item h4::before {
  content: '';
  width: 8px;
  height: 8px;
  background: #3DBBFF;
  border-radius: 50%;
  box-shadow: 0 0 10px rgba(0, 123, 255, 0.5);
  animation: pulse-dot 2s ease-in-out infinite;
}

@keyframes pulse-dot {
  0%, 100% {
    transform: scale(1);
    box-shadow: 0 0 10px rgba(0, 123, 255, 0.5);
  }
  50% {
    transform: scale(1.2);
    box-shadow: 0 0 20px rgba(0, 123, 255, 0.8);
  }
}

.highlight-item p {
  font-size: 1rem;
  line-height: 1.7;
  color: #e0e0e0;
  margin: 0;
  padding-left: 18px;
  position: relative;
}

.highlight-category.fronted {
  background: linear-gradient(135deg, rgba(52, 211, 153, 0.08), rgba(16, 185, 129, 0.05));
  border-color: rgba(52, 211, 153, 0.2);
}

.highlight-category.fronted::before {
  background: linear-gradient(90deg, #10b981, #059669, #10b981);
}

.highlight-category.fronted h3 {
  color: #10b981;
}

.highlight-category.fronted h3::after {
  background: linear-gradient(90deg, #10b981, #059669);
}

.highlight-category.fronted .highlight-item h4::before {
  background: #10b981;
  box-shadow: 0 0 10px rgba(16, 185, 129, 0.5);
}

.highlight-category.fronted .highlight-item::before {
  background: linear-gradient(180deg, #10b981, #059669);
}

.highlight-category.fronted:hover {
  border-color: rgba(52, 211, 153, 0.4);
  box-shadow: 0 15px 40px rgba(16, 185, 129, 0.2);
}

.highlight-category.backend {
  background: linear-gradient(135deg, rgba(245, 158, 11, 0.08), rgba(217, 119, 6, 0.05));
  border-color: rgba(245, 158, 11, 0.2);
}

.highlight-category.backend::before {
  background: linear-gradient(90deg, #f59e0b, #d97706, #f59e0b);
}

.highlight-category.backend h3 {
  color: #f59e0b;
}

.highlight-category.backend h3::after {
  background: linear-gradient(90deg, #f59e0b, #d97706);
}

.highlight-category.backend .highlight-item h4::before {
  background: #f59e0b;
  box-shadow: 0 0 10px rgba(245, 158, 11, 0.5);
}

.highlight-category.backend .highlight-item::before {
  background: linear-gradient(180deg, #f59e0b, #d97706);
}

.highlight-category.backend:hover {
  border-color: rgba(245, 158, 11, 0.4);
  box-shadow: 0 15px 40px rgba(245, 158, 11, 0.2);
}

.final-results .large-title {
  font-size: 5rem;
  font-weight: 700;
}

.final-results .large-subtitle {
  font-size: 1.8rem;
  color: #8b949e;
  margin-top: 10px;
  text-align: center;
}

.final-results .demo-info {
  margin-top: 50px;
  background: rgba(0,0,0,0.2);
  padding: 30px;
  border-radius: 15px;
  text-align: center;

}

.final-results .demo-info h2 {
  font-size: 32px;
  margin-bottom: 20px;
  text-align: center;
}

.final-results .demo-list {
  list-style: none;
  padding: 0;
  text-align: center;
}

.final-results .demo-list li {
  font-size: 1.2rem;
  margin-bottom: 10px;
  padding-left: 25px;
  position: relative;
}

.final-results .demo-list li::before {
  content: '✓';
  position: absolute;
  left: 0;
  color: #3DBBFF;
  font-weight: bold;
}

@media (max-width: 1200px) {
  .highlights-container {
    grid-template-columns: 1fr;
    gap: 30px;
    max-width: 800px;
  }

  .philosophy-grid-interactive {
    grid-template-columns: 1fr;
    max-width: 600px;
  }
}

@media (max-width: 768px) {
  .scroll-section {
    padding: 40px 20px;
  }

  .member-card.active {
    width: 90vw;
    flex-direction: column;
  }

  .member-card.active .member-initial-view {
    border-right: none;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    padding-right: 0;
    padding-bottom: 20px;
    width: 100%;
  }

  .philosophy-card-interactive.active {
    padding: 20px;
  }

  .hero h1.hero-title {
    font-size: 4rem;
  }

  .project-highlights h2, .design-philosophy h2, .team-interactive h2 {
    font-size: 2.5rem;
  }
}
</style>
