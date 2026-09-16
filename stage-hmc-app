  const { createApp, reactive } = Vue;

  const _preloaded = new Set();

  const app = createApp({
    name: "quiz",
    data() {
      return {
        cfg: window.quizConfig,
        currentNodeId: window.quizConfig.startId,
        answers: {},
        selectedSingle: null,
        selectedMulti: [],
        history: [],
        selectedProgram: null,
        selectedPlan: null,
        isModalOpen: false,
        activeModalId: null,
        devicePrices: {},
        planPrices: {},
        submissionId: null,
        MAKE_WEBHOOK_URL:
          "https://hook.us1.make.celonis.com/3if3fgwdr2bjfpcw2ljzxnowypkmwcn4",
        emailResults: { email: "" },
        isSubmitting: false,
        submissionSource: "",
        emailForResults: "",
        emailModalState: "form",
        emailModalError: "",
        bagEmail: "",
        hear: "",
        howHearOther: "",
        howHearRC: "",
        bagModalError: "",
        bagModalState: "form",
        terms: "false",
        otherText: "",
        sessionId: "",
      };
    },
    computed: {
      isShareProgram() {
        return this.resolvedProgramKey === "share";
      },
      isLevelProgram() {
        return (
          this.resolvedProgramKey === "level_1" ||
          this.resolvedProgramKey === "level_2"
        );
      },
      isHowHearOther() {
        return this.hear === "Other";
      },
      isHowHearRC() {
        return this.isShareProgram && this.hear === "Recovery Community";
      },
      canSubmitBagForm() {
        const email = String(this.bagEmail || "").trim();
        const hear = String(this.hear || "").trim();
        const other = String(this.howHearOther || "").trim();
        const rc = String(this.howHearRC || "").trim();

        if (!email || !hear || !this.terms) return false;
        if (this.isHowHearOther && !other) return false;
        if (this.isHowHearRC && !rc) return false;

        return true;
      },
      isRestartCtaNode() {
        const id = this.currentNode?.id;
        return (
          id === "qB2_criminalJustice_end_receiver" ||
          id === "qA2_criminalJustice_end_submitter"
        );
      },
      nextButtonAction() {
        return this.isRestartCtaNode ? this.restart : this.goNext;
      },
      canSubmitEmail() {
        const email = String(this.emailResults?.email || "").trim();
        if (!email) return false;

        const hear = String(this.hear || "").trim();
        if (!hear) return false;

        if (this.isHowHearOther && !String(this.howHearOther || "").trim())
          return false;
        if (this.isHowHearRC && !String(this.howHearRC || "").trim())
          return false;

        return true;
      },
      resolvedProgramDisplay() {
        return this.selectedPlanNode?.programDisplay || this.resolvedProgram;
      },
      finalSubtitleHtml() {
        const programKey = this.resolvedProgramKey;
        if (programKey === "share") {
          return "Soberlink is the <span class='u-bold'>ultimate investment in your health and relationships</span>.";
        }
        if (programKey === "level_1" || programKey === "level_2") {
          return "Soberlink is the <span class='u-bold'>ultimate investment in safety</span> and <span class='u-bold'>trust, </span> because time with your kids is priceless.";
        }
        return "";
      },
      userRoleRoute() {
        return this.answers["q1_useCase"] === "receiveResults"
          ? "receiver"
          : "submitter";
      },
      currentNode() {
        return this.getNodeById(this.currentNodeId);
      },
      resolvedProgram() {
        return this.selectedPlanNode?.program || null;
      },
      resolvedPlan() {
        return this.selectedPlanNode?.plan || null;
      },
      resolvedDeviceLine() {
        const n = this.currentNode;
        if (!n || n.type !== "final") return null;
        return this.displayDeviceName(n.device || "");
      },
      resolvedPricingLine() {
        const n = this.currentNode;
        if (!n || n.type !== "final") return null;
        if (!n.pricing) return null;

        const parts = [];
        if (n.pricing.monthly) parts.push(n.pricing.monthly);
        if (n.pricing.devicePrice) parts.push(n.pricing.devicePrice);
        if (n.pricing.commitment) parts.push(n.pricing.commitment);
        return parts.length ? parts.join(" • ") : null;
      },
      showNextButton() {
        const n = this.currentNode;
        if (!n) return false;
        if (n.type === "final") return false;
        if (n.type === "router") return false;
        return true;
      },
      canGoNext() {
        const n = this.currentNode;
        if (!n) return false;

        if (this.isRestartCtaNode) return true;

        if (n.type === "start") return true;
        if (n.type === "singleChoice") return !!this.selectedSingle;
        if (n.type === "multiChoice") return this.selectedMulti.length > 0;
        if (n.type === "info") return !!(n.primaryCta && n.primaryCta.nextId);
        if (n.type === "definition")
          return !!(n.primaryCta && n.primaryCta.nextId);
        if (n.type === "stories")
          return !!(n.primaryCta && n.primaryCta.nextId);
        if (n.type === "quote") return !!(n.primaryCta && n.primaryCta.nextId);
        if (n.type === "plan") return !!n.nextId;

        return false;
      },

      nextButtonLabel() {
        const n = this.currentNode;
        if (!n) return "Next";
        if (n.type === "singleChoice") {
          return this.selectedSingle ? "Next" : "Select One";
        }
        if (n.type === "multiChoice") {
          return this.selectedMulti.length > 0 ? "Next" : "Select Option(s)";
        }
        if (n.type === "quote") {
          return n.primaryCta?.label || "Continue";
        }
        if (n.type === "info") {
          return n.primaryCta?.label || "Next";
        }
        if (n.type === "definition") {
          return n.primaryCta?.label || "Next";
        }
        if (n.type === "stories") {
          return n.primaryCta?.label || "Continue";
        }
        if (n.type === "plan") {
          return this.planFooterCtaLabel?.() || n.primaryCta?.label || "Next";
        }
        if (n.primaryCta?.label) {
          return n.primaryCta.label;
        }
        return "Next";
      },

      activeModal() {
        if (!this.activeModalId) return null;
        return this.cfg.modals
          ? this.cfg.modals[this.activeModalId] || null
          : null;
      },
      progressPercent() {
        if (this.isRestartCtaNode) return 100;
        const completedSteps = this.history.length;
        const totalSteps = this.estimatedTotalSteps;

        if (!totalSteps) return 0;

        return Math.min(100, Math.round((completedSteps / totalSteps) * 100));
      },

      estimatedTotalSteps() {
        if (this.isRestartCtaNode) return this.history.length;

        const useCase = this.answers["q1_useCase"];
        if (!useCase) return 14;

        const programKey = this.resolvedProgramKey;

        if (useCase === "receiveResults") {
          if (programKey === "share") return 10;
          if (programKey === "level_2") return 13;
          if (programKey === "level_1") {
            const testingDays = this.answers["qB5L1_testingDays_receiver"];
            return testingDays === "needMoreThanTwenty" ? 12 : 14;
          }
          const freq = this.answers["qB4_monitoredClientFrequency"];
          if (freq === "parentingDaysOnly") return 14;
          if (freq === "everyDay") return 13;
          const reasons = this.answers["qB2_reasons_receiver"];
          const hasCustody =
            Array.isArray(reasons) && reasons.includes("childCustody");
          return hasCustody ? 13 : 10;
        }

        if (useCase === "submitTests") {
          if (programKey === "share") return 8;
          if (programKey === "level_2") {
            const context = this.answers["qA3_custody_context"];
            return context === "fullAbstinenceKeepKids" ? 10 : 11;
          }
          if (programKey === "level_1") {
            const testingDays = this.answers["qA6L1_testingDays_submitter"];
            return testingDays === "needMoreThanTwenty" ? 10 : 12;
          }
          const reasons = this.answers["qA2_reasons_submitter"];
          const hasCustody =
            Array.isArray(reasons) && reasons.includes("childCustody");
          if (!hasCustody && reasons) return 8;
          const freq = this.answers["qA4_testingFrequency_submitter"];
          if (freq === "parentingDaysOnly") return 12;
          return 11;
        }

        return 13;
      },
      selectedPlanNode() {
        if (!this.selectedPlan) return null;
        return this.getNodeById(this.selectedPlan);
      },

      resolvedProgramKey() {
        return this.selectedPlanNode?.programKey || "";
      },

      resolvedPlanKey() {
        return this.selectedPlanNode?.planKey || "";
      },
    },
    watch: {
      currentNodeId: {
        immediate: true,
        handler() {
          this.resetSelectionForNode(this.currentNode);
          this.autoAdvanceIfRouter();

          const node = this.currentNode;
          if (
            ["info", "quote", "definition", "stories", "start"].includes(
              node?.type,
            )
          ) {
            const nextId = node?.primaryCta?.nextId;
            if (nextId) {
              const dest = this.getNodeById(nextId);
              this.preloadImages(this.extractNodeImages(dest));
            }
          }
        },
      },
      hear(newVal) {
        if (newVal !== "other") {
          this.howHearOther = "";
        }

        if (newVal !== "recoveryCommunity") {
          this.howHearRC = "";
        }
      },
    },
    mounted() {
      const tryLoad = () => {
        const dp = window.sl_global_device_commitment_pricing;
        const pp = window.sl_global_plan_pricing;
        if (dp && typeof dp === "object") this.devicePrices = dp;
        if (pp && typeof pp === "object") this.planPrices = pp;
        if (this.devicePrices?.connect && this.planPrices?.share) return;
        setTimeout(tryLoad, 50);
      };
      tryLoad();

      const preloadUrls = [
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69dd3eba4d7518cba0f86ff8_2.avif",
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69dec46ee57f9e618ed30e42_1.avif",
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69b1d7bbdcbd0ec72e582683_Icon-cellular-device-v2.avif",
        "https://cdn.prod.website-files.com/5f001b69b01d2658098e3f5c/69dd6318edf2aeba0062eda4_Icon-Text-2.avif",
      ];
      this.preloadImages(preloadUrls);
    },

    methods: {
      preloadImage(url) {
        if (!url || _preloaded.has(url)) return;
        const img = new Image();
        img.onload = img.onerror = () => _preloaded.add(url);
        img.src = url;
      },
      preloadImages(urls = []) {
        [...new Set(urls)].forEach((url) => this.preloadImage(url));
      },
      extractNodeImages(node) {
        if (!node) return [];
        const urls = [];
        if (node.imageUrl) urls.push(node.imageUrl);
        (node.options || []).forEach((opt) => {
          if (opt.icon?.url) urls.push(opt.icon.url);
          if (opt.badge?.icon?.url) urls.push(opt.badge.icon.url);
        });
        (node.stories || []).forEach((s) => {
          if (s.image?.url) urls.push(s.image.url);
          if (s.icon?.url) urls.push(s.icon.url);
        });
        if (node.infoIcon?.url) urls.push(node.infoIcon.url);

        const modalId = node.infoLink?.id;
        if (modalId) {
          const modal = this.cfg.modals?.[modalId];
          (modal?.items || []).forEach((item) => {
            if (item.img?.url) urls.push(item.img.url);
          });
        }
        return urls.filter(Boolean);
      },
      goNext() {
        const node = this.currentNode;
        if (!node || !this.canGoNext) return;
        if (node.type === "singleChoice" || node.type === "multiChoice") {
          this.commitAnswer(node);
          if (this.selectedMulti.includes("other") && this.otherText.trim()) {
            this.answers[node.id + "_otherText"] = this.otherText.trim();
          }
        }
        this.commitPlanSelectionIfNeeded(node);
        const nextId = this.computeNextId(node);
        if (!nextId) return;
        this.history.push(node.id);
        this.currentNodeId = nextId;
        this.$nextTick(() => {
          const el = document.getElementById("quiz");
          if (!el) return;
          const navOffset = 185;
          const y =
            el.getBoundingClientRect().top + window.pageYOffset - navOffset;
          window.scrollTo({ top: y, behavior: "smooth" });
        });
      },
      getMonitoredClientCheckboxEl() {
        return document.getElementById("monitoredClientConfirm");
      },

      isMonitoredClientConfirmed() {
        return !!this.terms;
      },
      validateMonitoredClientCheckbox() {
        const el = this.getMonitoredClientCheckboxEl();
        if (!el) return true;

        if (!this.isMonitoredClientConfirmed()) {
          el.setCustomValidity(
            "Please confirm this is the monitored client's email and that monitoring begins after checkout.",
          );
          el.reportValidity();
          return false;
        }
        el.setCustomValidity("");
        return true;
      },
      clearMonitoredClientTooltip() {
        const el = this.getMonitoredClientCheckboxEl();
        if (el) el.setCustomValidity("");
      },
      async fetchSessionToken() {
        return "No More Authentication";
      },
      async createEcommerceSession(bearerToken) {
        const sessionService = window.sl_global_session_service_endpoint;
        const sessionUri = `${sessionService}/sessions`;

        const response = await fetch(sessionUri, {
          method: "POST",
          headers: {
            Accept: "application/json",
            "Content-Type": "application/json",
            Authorization: `Bearer ${bearerToken}`,
          },
        });
        if (!response.ok) {
          const text = await response.text();
          throw new Error(`Create sess fail: ${response.status}`);
        }
        const jsonObj = await response.json();
        return jsonObj.sessionId.toString();
      },
      async updateEcommerceSession(ecommerceSession, bearerToken) {
        const sessionService = window.sl_global_session_service_endpoint;
        const sessionUri = `${sessionService}/sessions`;
        const response = await fetch(
          `${sessionUri}/${ecommerceSession.sessionId}`,
          {
            method: "PUT",
            headers: {
              Accept: "application/json",
              "Content-Type": "application/json",
              Authorization: `Bearer ${bearerToken}`,
            },
            body: JSON.stringify(ecommerceSession),
          },
        );
        if (!response.ok) {
          const text = await response.text();
          throw new Error(`Update sess fai: ${response.status}`);
        }
        return await response.json();
      },
      async getEcommerceSession(sessionId, bearerToken) {
        const sessionService = window.sl_global_session_service_endpoint;
        const sessionUri = `${sessionService}/sessions`;
        const response = await fetch(`${sessionUri}/${sessionId}`, {
          method: "GET",
          headers: {
            Accept: "application/json",
            "Content-Type": "application/json",
            Authorization: `Bearer ${bearerToken}`,
          },
        });

        if (!response.ok) {
          const text = await response.text();
          throw new Error(
            `Get sess fail ${sessionId}: ${response.status} ${text}`,
          );
        }
        return await response.json();
      },
      getBagSessionProgram() {
        return this.resolvedProgramKey || "";
      },
      getBagSessionPlan() {
        return this.resolvedPlanKey || "";
      },
      getBagSessionDevice() {
        const finalNode =
          this.currentNode && this.currentNode.type === "final"
            ? this.currentNode
            : null;
        const rawDevice = String(finalNode?.device || "")
          .trim()
          .toLowerCase();
        if (
          rawDevice === "connect" ||
          rawDevice === "s7" ||
          rawDevice === "soberlink 7.0"
        ) {
          return this.cfg.activeConnectVariant === "s7" ? "s7" : "connect";
        }
        if (rawDevice === "cellular 2") {
          return "cellular 2";
        }
        return "";
      },
      getBagSessionRentOrBuy() {
        const finalNode =
          this.currentNode && this.currentNode.type === "final"
            ? this.currentNode
            : null;

        const ownership = String(finalNode?.ownership || "")
          .trim()
          .toLowerCase();

        if (ownership === "own") return "buy";

        if (ownership === "rent") {
          return String(finalNode?.pricing?.monthlyRef?.commitment || "");
        }
        return "";
      },
      getBagSessionItemIds() {
        const program = this.getBagSessionProgram();
        const plan = this.getBagSessionPlan();
        const device = this.getBagSessionDevice();
        const rentOrBuy = this.getBagSessionRentOrBuy();

        const id1 = window.sl_global_net_suite_item_id_1?.[program]?.[plan];
        const id2 = window.sl_global_net_suite_item_id_2?.[device]?.[rentOrBuy];

        return {
          program,
          plan,
          device,
          rentOrBuy,
          id1,
          id2,
        };
      },
      handleBagSubmitClick(e) {
        e.preventDefault();

        if (!this.canSubmitBagForm || this.isSubmitting) return;

        this.submitBagResults();
      },
      onViewResultsInBag() {
        this.bagModalState = "form";
        this.bagModalError = "";
        this.resetBagResultsForm();
        this.openModal("bagResults");
      },
      resetBagResultsForm() {
        this.bagEmail = "";
        this.hear = "";
        this.howHearOther = "";
        this.howHearRC = "";
        this.terms = false;
      },
      validateBagResultsForm() {
        const email = String(this.bagEmail || "").trim();
        const hear = String(this.hear || "").trim();
        const other = String(this.howHearOther || "").trim();
        const rc = String(this.howHearRC || "").trim();

        if (!email) {
          this.bagModalError = this.isShareProgram
            ? "Please enter the monitored client email."
            : "Please enter your email.";
          return false;
        }
        const emailOk = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
        if (!emailOk) {
          this.bagModalError = this.isShareProgram
            ? "Please enter a valid monitored client email."
            : "Please enter a valid email address.";
          return false;
        }

        if (!hear) {
          this.bagModalError = "Please select how you heard about us.";
          return false;
        }

        if (this.isHowHearOther && !other) {
          this.bagModalError = "Please specify how you heard about us.";
          return false;
        }

        if (this.isHowHearRC && !rc) {
          this.bagModalError = "Please tell us which recovery community.";
          return false;
        }

        this.bagModalError = "";
        return true;
      },
      async submitBagResults(e) {
        if (e && e.preventDefault) e.preventDefault();
        if (this.isSubmitting) return;

        const isValid = this.validateBagResultsForm();
        if (!isValid) return;

        const isCheckboxValid = this.validateMonitoredClientCheckbox();
        if (!isCheckboxValid) return;

        try {
          this.isSubmitting = true;
          this.bagModalError = "";
          this.submissionSource = "bag";
          this.emailForResults = this.bagEmail || "";

          if (!this.submissionId) {
            this.submissionId =
              typeof crypto !== "undefined" && crypto.randomUUID
                ? crypto.randomUUID()
                : `sub_${Date.now()}_${Math.random().toString(16).slice(2)}`;
          }

          const { program, plan, device, rentOrBuy, id1, id2 } =
            this.getBagSessionItemIds();

          if (!program || !plan || !device || !rentOrBuy) {
            throw new Error(
              "Missing required program, plan, device, or rent/buy values for session creation.",
            );
          }

          if (!id1 || !id2) {
            throw new Error(`Missing NS ids`);
          }

          const bearerToken = await this.fetchSessionToken();
          const sessionId = await this.createEcommerceSession(bearerToken);

          const updatePayload = {
            sessionId,
            startPage: 1,
            shoppingCartItemGroups: [
              {
                shoppingCartItems: [
                  { netSuiteItemId: id2 },
                  { netSuiteItemId: id1 },
                ],
                quantity: 1,
              },
            ],
            showDevices: true,
            showMTC: true,
          };

          await this.updateEcommerceSession(updatePayload, bearerToken);
          const session = await this.getEcommerceSession(
            sessionId,
            bearerToken,
          );
          this.sessionId = session.sessionId;

          await this.submitToMake();

          const redirectUrl = window.sl_global_cart_redirect_url;
          if (!redirectUrl) {
            throw new Error("Missing sl_global_cart_redirect_url");
          }

          const url = `${redirectUrl}?sessionId=${session.sessionId}`;
          window.location.href = url;
        } catch (err) {
          console.error(err);
          this.bagModalError = "Something went wrong. Please try again.";
        } finally {
          this.isSubmitting = false;
        }
      },
      async submitEmailResults(e) {
        if (e && e.preventDefault) e.preventDefault();

        if (!this.canSubmitEmail || this.isSubmitting) return;

        const email = String(this.emailResults?.email || "").trim();

        this.emailModalError = "";

        if (!email) {
          this.emailModalState = "form";
          this.emailModalError = "Please enter your email address.";
          return;
        }

        const emailOk = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
        if (!emailOk) {
          this.emailModalState = "form";
          this.emailModalError = "Please enter a valid email address.";
          return;
        }

        const hear = String(this.hear || "").trim();
        if (!hear) {
          this.emailModalState = "form";
          this.emailModalError = "Please select how you heard about us.";
          return;
        }
        if (this.isHowHearOther && !String(this.howHearOther || "").trim()) {
          this.emailModalState = "form";
          this.emailModalError = "Please specify how you heard about us.";
          return;
        }
        if (this.isHowHearRC && !String(this.howHearRC || "").trim()) {
          this.emailModalState = "form";
          this.emailModalError = "Please tell us which recovery community.";
          return;
        }

        this.submissionSource = "email";
        this.emailForResults = email;

        if (!this.submissionId) {
          this.submissionId =
            typeof crypto !== "undefined" && crypto.randomUUID
              ? crypto.randomUUID()
              : `sub_${Date.now()}_${Math.random().toString(16).slice(2)}`;
        }

        try {
          this.isSubmitting = true;

          const finalNode =
            this.currentNode && this.currentNode.type === "final"
              ? this.currentNode
              : null;

          if (this.canAddToCart(finalNode)) {
            const { id1, id2 } = this.getBagSessionItemIds();

            if (!id1 || !id2) {
              throw new Error("Missing NS ids.");
            }

            const bearerToken = await this.fetchSessionToken();
            const sessionId = await this.createEcommerceSession(bearerToken);

            const updatePayload = {
              sessionId,
              startPage: 1,
              shoppingCartItemGroups: [
                {
                  shoppingCartItems: [
                    { netSuiteItemId: id2 },
                    { netSuiteItemId: id1 },
                  ],
                  quantity: 1,
                },
              ],
              showDevices: true,
              showMTC: true,
            };

            await this.updateEcommerceSession(updatePayload, bearerToken);
            const session = await this.getEcommerceSession(
              sessionId,
              bearerToken,
            );
            this.sessionId = session.sessionId;
          }

          await this.submitToMake();
          this.emailModalState = "success";
        } catch (err) {
          console.error(err);
          this.emailModalState = "error";
          this.emailModalError = "Something went wrong. Please try again.";
        } finally {
          this.isSubmitting = false;
        }
      },
      renderDeviceMetaHtml(html) {
        if (!html) return "";

        return String(html).replaceAll(
          "{CONNECT_FAMILY_LABEL}",
          this.displayDeviceName("connect"),
        );
      },
      normalizeDeviceKey(device) {
        const d = String(device || "")
          .trim()
          .toLowerCase();

        if (d === "connect" || d === "soberlink 7.0" || d === "s7")
          return "connect";
        if (d === "cellular 2") return "cellular 2";

        return d;
      },
      displayDeviceParam(device) {
        const key = this.normalizeDeviceKey(device);

        if (key === "connect") {
          return this.cfg.activeConnectVariant === "s7" ? "s7" : "connect";
        }

        if (key === "cellular 2") {
          return "cellular 2";
        }

        return key;
      },
      activeDeviceVariant(device) {
        const key = this.normalizeDeviceKey(device);

        if (key === "connect") {
          return this.cfg.activeConnectVariant || "connect";
        }
        return "default";
      },
      displayDeviceName(device) {
        const key = this.normalizeDeviceKey(device);
        const variant = this.activeDeviceVariant(device);

        const cfg = this.cfg.deviceVariants?.[key];
        if (!cfg) return device || "";

        const variantCfg = cfg[variant] || cfg.default;
        return variantCfg?.label || device || "";
      },
      displayDeviceImage(device, fallbackUrl = "") {
        const key = this.normalizeDeviceKey(device);
        const variant = this.activeDeviceVariant(device);

        const cfg = this.cfg.deviceVariants?.[key];
        if (!cfg) return fallbackUrl || "";

        const variantCfg = cfg[variant] || cfg.default;
        return variantCfg?.imageUrl || fallbackUrl || "";
      },
      planFooterHtml() {
        const footer = this.cfg.planFooters?.[this.userRoleRoute];
        if (!footer) return "";

        let html = footer.textHtml || footer.text || "";
        const tokens = footer.textTokens || {};

        for (const [tokenName, ref] of Object.entries(tokens)) {
          const n = this.resolvePriceRef(ref);
          const replacement = typeof n === "number" ? this.money(n) : "";
          html = html.replaceAll(`{${tokenName}}`, replacement);
        }

        return html;
      },
      planFooterCtaLabel() {
        return this.cfg.planFooters?.[this.userRoleRoute]?.ctaLabel || "Next";
      },
      planScreenPriceHtml(node) {
        if (!node?.priceRef) return "";

        const n = this.resolvePriceRef(node.priceRef);
        if (typeof n !== "number") return "";

        const cadence =
          node.priceRef?.cadence === "mo"
            ? "<span style='font-size:18px;'>/mo</span>"
            : "";

        return `${this.money(n)}${cadence}`;
      },

      buildAddToCartUrlWithAnchor() {
        const base = this.buildAddToCartUrl();
        if (!base) return "";

        const url = new URL(base);

        const hasDevice = !!url.searchParams.get("device");
        const hasRentOrBuy = !!url.searchParams.get("rentOrBuy");
        const hasPlan = !!url.searchParams.get("plan");

        if (hasDevice && hasRentOrBuy && hasPlan) {
          url.hash = "step3";
        }

        return url.toString();
      },
      onStoryClick(story) {
        if (!story?.opensModalId) return;
        this.openModal(story.opensModalId);
      },
      finalDevicePriceHtml(res) {
        const pricing = res?.pricing;
        if (!pricing) return "";

        const ref = pricing.devicePriceRef;
        const n = this.resolvePriceRef(ref);

        if (typeof n !== "number") return pricing.devicePrice || "";

        const prefix = pricing.devicePricePrefix || "";
        const suffix = pricing.devicePriceSuffix || "";
        return `${prefix}${this.money(n)}${suffix}`;
      },
      resolvePriceRef(ref) {
        if (!ref) return null;

        if (ref.kind === "plan") {
          const val = this.planPrices?.[ref.program]?.[ref.tier];
          return typeof val === "number" ? val : null;
        }

        if (ref.kind === "device") {
          const resolvedDevice = this.displayDeviceParam(ref.device);
          const val = this.devicePrices?.[resolvedDevice]?.[ref.commitment];
          return typeof val === "number" ? val : null;
        }

        if (ref.kind === "deviceMin") {
          const commitmentKey = ref.commitment;
          if (!commitmentKey) return null;

          const vals = Object.entries(this.devicePrices || {})
            .filter(([key]) => key !== "connect")
            .map(([, deviceObj]) => deviceObj?.[commitmentKey])
            .filter((v) => typeof v === "number");

          if (!vals.length) return null;
          return Math.min(...vals);
        }

        return null;
      },
      money(n) {
        if (typeof n !== "number") return "";
        return `$${n}`;
      },
      optionLabelHtml(opt) {
        if (!opt?.labelHtml) return "";
        const n = this.resolvePriceRef(opt.priceRef);
        if (typeof n !== "number") return opt.labelHtml;
        return opt.labelHtml.replace("{PRICE}", this.money(n));
      },
      optionPriceHtml(opt) {
        if (opt.priceHtml) return opt.priceHtml;
        const n = this.resolvePriceRef(opt.priceRef);
        if (typeof n !== "number") return "";
        const cadence =
          opt.priceRef?.cadence === "mo"
            ? "<span style='font-size:12px;'>/mo</span>"
            : "";
        return `${this.money(n)}${cadence}`;
      },

      finalMonthlyHtml(res) {
        const ref = res?.pricing?.monthlyRef;
        const n = this.resolvePriceRef(ref);
        if (typeof n !== "number") return res?.pricing?.monthly || "";
        return `${this.money(n)}<span style='font-size:12px;'>/mo</span>`;
      },
      renderNodeText(node) {
        if (!node) return "";
        let html = node.textHtml || "";

        if (!html && node.text) {
          html = String(node.text).replace(/\n/g, "<br>");
        }

        const tokens = node.textTokens || {};
        for (const [tokenName, ref] of Object.entries(tokens)) {
          const n = this.resolvePriceRef(ref);
          const replacement = typeof n === "number" ? this.money(n) : "";
          html = html.replaceAll(`{${tokenName}}`, replacement);
        }

        return html;
      },
      getNodeById(id) {
        if (!id) return null;
        const node =
          (this.cfg.nodes && this.cfg.nodes[id]) ||
          (this.cfg.results && this.cfg.results[id]) ||
          null;
        return this.normalizeNode(node);
      },
      normalizeNode(node) {
        if (!node) return node;

        if (node.text == null) node.text = "";
        if (node.textHtml == null) node.textHtml = "";

        if (node.type === "singleChoice") {
          node.options = node.options || [];
        }
        if (node.type === "multiChoice") {
          node.options = node.options || [];
          node.rules = node.rules || [];
          if (node.defaultNextId === undefined) node.defaultNextId = null;
        }
        if (node.type === "info") {
          node.links = node.links || [];
          node.primaryCta = node.primaryCta || {
            label: "Continue",
            nextId: null,
          };
        }
        if (node.type === "definition") {
          node.links = node.links || [];
          node.primaryCta = node.primaryCta || {
            label: "Continue",
            nextId: null,
          };
        }
        if (node.type === "stories") {
          node.stories = node.stories || [];
          node.primaryCta = node.primaryCta || {
            label: "Continue",
            nextId: null,
          };
        }
        if (node.type === "quote") {
          node.primaryCta = node.primaryCta || {
            label: "Continue",
            nextId: null,
          };
          node.person = node.person || {};
          node.person.image = node.person.image || {};
        }
        if (node.type === "plan") {
          if (!node.nextId && node.primaryCta && node.primaryCta.nextId)
            node.nextId = node.primaryCta.nextId;
        }
        if (node.type === "final") {
          node.nextId = null;
        }
        if (node.type === "router") {
          node.rules = node.rules || [];
          if (node.defaultNextId === undefined) node.defaultNextId = null;
        }
        return node;
      },
      splitLines(text) {
        if (!text) return [];
        return String(text)
          .split("\n")
          .filter((l) => l.trim() !== "");
      },
      resetSelectionForNode(node) {
        this.otherText = "";
        this.selectedSingle = null;
        this.selectedMulti = [];
        if (!node) return;
        const prev = this.answers[node.id];
        if (node.type === "singleChoice" && typeof prev === "string") {
          this.selectedSingle = prev;
        } else if (node.type === "multiChoice" && Array.isArray(prev)) {
          this.selectedMulti = [...prev];
        }
      },
      evalRouterNextId(routerNode) {
        const rules = routerNode.rules || [];
        for (const rule of rules) {
          if (rule.whenEquals) {
            const { nodeId, value } = rule.whenEquals;
            if (this.answers[nodeId] === value) return rule.nextId;
          }
        }
        return routerNode.defaultNextId || null;
      },
      autoAdvanceIfRouter() {
        const n = this.currentNode;
        if (!n || n.type !== "router") return;

        const nextId = this.evalRouterNextId(n) || "res_generic_contact";
        this.currentNodeId = nextId;
      },
      computeNextIdFromSingleChoice(node, value) {
        const opt = (node.options || []).find((o) => o.value === value);
        return opt ? opt.nextId : null;
      },
      computeNextIdFromMultiChoice(node, values) {
        const chosen = Array.isArray(values) ? values : [];

        for (const rule of node.rules || []) {
          if (rule.whenOnly) {
            const only = rule.whenOnly;
            const exactMatch =
              chosen.length === only.length &&
              only.every((v) => chosen.includes(v));
            if (exactMatch) return rule.nextId;
          }

          const anyOf = rule.whenIncludesAnyOf || [];
          if (anyOf.some((v) => chosen.includes(v))) return rule.nextId;
        }

        return node.defaultNextId || null;
      },
      computeNextId(node) {
        if (!node) return null;
        if (node.type === "start")
          return node.primaryCta && node.primaryCta.nextId
            ? node.primaryCta.nextId
            : null;

        if (node.type === "singleChoice")
          return this.computeNextIdFromSingleChoice(node, this.selectedSingle);
        if (node.type === "multiChoice")
          return this.computeNextIdFromMultiChoice(node, this.selectedMulti);
        if (node.type === "info")
          return node.primaryCta && node.primaryCta.nextId
            ? node.primaryCta.nextId
            : null;
        if (node.type === "definition")
          return node.primaryCta && node.primaryCta.nextId
            ? node.primaryCta.nextId
            : null;
        if (node.type === "stories")
          return node.primaryCta && node.primaryCta.nextId
            ? node.primaryCta.nextId
            : null;
        if (node.type === "quote")
          return node.primaryCta && node.primaryCta.nextId
            ? node.primaryCta.nextId
            : null;
        if (node.type === "plan") return node.nextId || null;

        return null;
      },
      commitAnswer(node) {
        if (!node) return;
        if (node.type === "singleChoice")
          this.answers[node.id] = this.selectedSingle;
        if (node.type === "multiChoice")
          this.answers[node.id] = [...this.selectedMulti];
      },
      commitPlanSelectionIfNeeded(node) {
        if (!node) return;

        if (node.type === "plan") {
          this.selectedPlan = node.id;
        }
      },
      goBack() {
        if (!this.history.length) return;
        const prevId = this.history.pop();
        this.currentNodeId = prevId;
        this.$nextTick(() => {
          const el = document.getElementById("quiz");
          if (!el) return;

          const navOffset = 132;

          const y =
            el.getBoundingClientRect().top + window.pageYOffset - navOffset;

          window.scrollTo({
            top: y,
            behavior: "smooth",
          });
        });
      },
      restart() {
        this.currentNodeId = this.cfg.startId;
        this.answers = {};
        this.history = [];

        this.selectedSingle = null;
        this.selectedMulti = [];
        this.selectedPlan = null;

        this.isSubmitting = false;
        this.submissionSource = "";
        this.emailForResults = "";
        if (this.emailResults) this.emailResults.email = "";

        this.submissionId = null;
        this.sessionId = "";

        this.closeModal();
      },
      handleLink(linkObj) {
        if (!linkObj) return;
        if (linkObj.type === "lightbox" && linkObj.id) {
          this.openModal(linkObj.id);
        }
      },
      onEmailRecommendations() {
        this.submissionSource = "email";
        this.emailModalState = "form";
        this.emailModalError = "";
        this.emailForResults = this.emailResults.email || "";
        this.hear = "";
        this.howHearOther = "";
        this.howHearRC = "";
        this.openModal("emailResults");
      },
      toggleMulti(value) {
        if (this.selectedMulti.includes(value)) {
          this.selectedMulti = this.selectedMulti.filter((v) => v !== value);
        } else {
          this.selectedMulti.push(value);
        }
      },
      handleNext(e) {
        e.preventDefault();

        if (!this.canGoNext) return;

        this.goNext();
      },
      handleBack(e) {
        e.preventDefault();

        if (this.history.length === 0) return;

        this.goBack();
      },
      onSelectSingle(e, opt) {
        if (e && e.preventDefault) e.preventDefault();
        this.selectedSingle = opt.value;

        if (opt.nextId) {
          const dest = this.getNodeById(opt.nextId);
          this.preloadImages(this.extractNodeImages(dest));

          const afterId = dest?.primaryCta?.nextId;
          if (afterId) {
            const after = this.getNodeById(afterId);
            if (after) this.preloadImages(this.extractNodeImages(after));
          }
        }
      },
      onToggleMulti(e, value) {
        if (e && e.preventDefault) e.preventDefault();
        this.toggleMulti(value);

        const node = this.currentNode;
        (node?.rules || []).forEach((rule) => {
          if (rule.nextId) {
            const dest = this.getNodeById(rule.nextId);
            this.preloadImages(this.extractNodeImages(dest));
          }
        });
      },
      onInfoIconClick(e, node) {
        if (e && e.preventDefault) e.preventDefault();
        if (node && node.infoLink) this.handleLink(node.infoLink);
      },
      openModal(modalId) {
        this.activeModalId = modalId;
        this.isModalOpen = true;

        document.documentElement.classList.add("is-modal-open");
        document.body.classList.add("is-modal-open");
      },
      closeModal() {
        this.isModalOpen = false;
        this.activeModalId = null;
        this.bagModalError = "";
        this.emailModalError = "";
        document.documentElement.classList.remove("is-modal-open");
        document.body.classList.remove("is-modal-open");
      },
      stripHtml(s) {
        return String(s || "")
          .replace(/<[^>]*>/g, "")
          .trim();
      },
      getQuestionText(node) {
        const raw = node?.textHtml || node?.text || "";
        return this.stripHtml(String(raw).replace(/\n/g, " "));
      },
      getOptionLabel(node, value) {
        const opt = (node?.options || []).find((o) => o.value === value);
        if (!opt) return "";

        const html = this.optionLabelHtml(opt);
        return this.stripHtml(html);
      },
      buildSubmissionRow() {
        if (!this.submissionId) {
          this.submissionId =
            typeof crypto !== "undefined" && crypto.randomUUID
              ? crypto.randomUUID()
              : `sub_${Date.now()}_${Math.random().toString(16).slice(2)}`;
        }
        const finalNode =
          this.currentNode && this.currentNode.type === "final"
            ? this.currentNode
            : null;

        const addToCartUrl = this.buildAddToCartUrlWithAnchor();

        let rentOrBuy = "";
        const ownership = String(finalNode?.ownership || "")
          .trim()
          .toLowerCase();
        if (ownership === "rent") {
          rentOrBuy = String(finalNode?.pricing?.monthlyRef?.commitment || "");
        } else if (ownership === "own") {
          rentOrBuy = "buy";
        }

        const row = {
          submissionId: this.submissionId,
          quizVersion: this.cfg?.version || "",
          submittedAtIso: new Date().toISOString(),
          sessionId: this.sessionId || "",
          source: this.submissionSource || "",

          email: this.emailForResults || "",

          programKey: this.resolvedProgramKey || "",
          planKey: this.resolvedPlanKey || "",

          programLabel: this.resolvedProgram || "",
          planLabel: this.resolvedPlan || "",

          finalResultId: finalNode?.id || "",
          device: this.displayDeviceParam(finalNode?.device || ""),
          deviceLabel: this.displayDeviceName(finalNode?.device || ""),
          ownership: finalNode?.ownership || "",
          rentOrBuy,
          answersJson: JSON.stringify(this.answers || {}),

          addToCartUrl,
        };

        const monthly = this.resolvePriceRef(finalNode?.pricing?.monthlyRef);
        const devicePrice = this.resolvePriceRef(
          finalNode?.pricing?.devicePriceRef,
        );
        if (typeof monthly === "number") row.finalMonthly = monthly;
        if (typeof devicePrice === "number") row.finalDevicePrice = devicePrice;

        for (const [nodeId, ans] of Object.entries(this.answers || {})) {
          const node = this.getNodeById(nodeId);

          row[nodeId] = Array.isArray(ans) ? ans.join("|") : ans;

          if (node) row[`${nodeId}_question`] = this.getQuestionText(node);

          if (node?.type === "singleChoice" && typeof ans === "string") {
            row[`${nodeId}_label`] = this.getOptionLabel(node, ans);

            const opt = (node.options || []).find((o) => o.value === ans);
            const n = this.resolvePriceRef(opt?.priceRef);
            if (typeof n === "number") row[`${nodeId}_price`] = n;
          }

          if (node?.type === "multiChoice" && Array.isArray(ans)) {
            const labels = ans
              .map((v) => this.getOptionLabel(node, v))
              .filter(Boolean);
            row[`${nodeId}_label`] = labels.join(" | ");
          }
        }
        if (
          this.submissionSource === "bag" ||
          this.submissionSource === "email"
        ) {
          row.hear = this.hear || "";
          row.howHearOther = this.howHearOther || "";
          row.howHearRC = this.howHearRC || "";
        }

        if (this.submissionSource === "bag") {
          row.bagEmail = this.bagEmail || "";

          row.monitoredClientEmail = this.isShareProgram
            ? this.bagEmail || ""
            : "";
          row.userEmail = this.isLevelProgram ? this.bagEmail || "" : "";
        }

        return row;
      },
      async submitToMake() {
        if (!this.MAKE_WEBHOOK_URL) {
          throw new Error("MAKE_WEBHOOK_URL is missing");
        }

        const payload = this.buildSubmissionRow();

        const res = await fetch(this.MAKE_WEBHOOK_URL, {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify(payload),
        });

        if (!res.ok) {
          const text = await res.text();
          throw new Error(`Make webhook failed: ${res.status} ${text}`);
        }
        return true;
      },
      normalizePlanParam(plan) {
        return String(plan || "")
          .trim()
          .toLowerCase();
      },
      getParentUrlForProgram(program) {
        const p = String(program || "")
          .trim()
          .toLowerCase();
        if (p === "share")
          return "https://www.soberlink.com/healthcare/share-program-get-started";
        if (p.includes("level_1") || p === "level1" || p === "level 1")
          return "https://www.soberlink.com/divorce/family-law-level-1-get-started";
        if (p.includes("level_2") || p === "level2" || p === "level 2")
          return "https://www.soberlink.com/divorce/family-law-level-2-get-started";
        return "";
      },
      buildAddToCartUrl() {
        const finalNode =
          this.currentNode && this.currentNode.type === "final"
            ? this.currentNode
            : null;

        const planNode = this.selectedPlan
          ? this.getNodeById(this.selectedPlan)
          : null;

        const rawProgramKey = planNode?.programKey || "";
        const planKey = planNode?.planKey || "";

        const programKey =
          rawProgramKey === "level1"
            ? "level_1"
            : rawProgramKey === "level2"
              ? "level_2"
              : rawProgramKey;

        const parent = this.getParentUrlForProgram(programKey);
        if (!parent) return "";

        const deviceParam = this.displayDeviceParam(finalNode?.device || "");

        let rentOrBuy = "";
        const ownership = String(finalNode?.ownership || "")
          .trim()
          .toLowerCase();

        if (ownership === "rent") {
          const c = finalNode?.pricing?.monthlyRef?.commitment;
          rentOrBuy = c ? String(c) : "rent 365";
        } else if (ownership === "own") {
          rentOrBuy = "buy";
        }

        const url = new URL(parent);

        if (deviceParam) url.searchParams.set("device", deviceParam);
        if (rentOrBuy) url.searchParams.set("rentOrBuy", rentOrBuy);

        const planParam = this.normalizePlanParam(planKey);

        if (planParam) url.searchParams.set("plan", planParam);

        return url.toString();
      },

      finalPlanPriceHtml(finalNode, planNode) {
        if (!planNode?.programKey || !planNode?.planKey) return "";

        const pricing = window.sl_global_plan_pricing || {};

        const programKey =
          planNode.programKey === "level1"
            ? "level_1"
            : planNode.programKey === "level2"
              ? "level_2"
              : planNode.programKey;

        const price = pricing?.[programKey]?.[planNode.planKey];

        if (price === undefined || price === null) return "";

        return `$${price}<span style='font-size: 12px;'>/mo</span>`;
      },
      programKeyFromLabel(label) {
        const s = String(label || "")
          .trim()
          .toLowerCase();
        if (s === "share") return "share";
        if (s.includes("level 1")) return "level_1";
        if (s.includes("level 2")) return "level_2";
        return "";
      },
      tierKeyFromLabel(label) {
        const s = String(label || "")
          .trim()
          .toLowerCase();
        if (s.includes("basic")) return "basic";
        if (s.includes("plus")) return "plus";
        if (s.includes("premium")) return "premium";
        return "";
      },
      finalDeviceTitle(finalNode) {
        const ownership = String(finalNode?.ownership || "").toLowerCase();
        const deviceLabel =
          this.displayDeviceName(finalNode?.device || "") || "Device";

        if (ownership === "rent") {
          const c = String(finalNode?.pricing?.monthlyRef?.commitment || "");
          if (c.includes("120")) return `120-Day ${deviceLabel} Rental`;
          if (c.includes("365")) return `365-Day ${deviceLabel} Rental`;
          return `${deviceLabel} Rental`;
        }

        if (ownership === "own") return `${deviceLabel} Purchase`;

        return "Device";
      },
      finalDeviceSubtitle(finalNode) {
        const device = String(finalNode?.device || "").trim();
        if (device.toLowerCase().includes("monitored client"))
          return "Monitored Client to Choose";
        return "";
      },
      finalDevicePriceRightHtml(finalNode) {
        const ownership = String(finalNode?.ownership || "").toLowerCase();

        if (ownership === "rent") return this.finalMonthlyHtml(finalNode);
        if (ownership === "own") return this.finalDevicePriceHtml(finalNode);

        return "";
      },

      finalDeviceFootnote(finalNode) {
        const ownership = String(finalNode?.ownership || "").toLowerCase();
        if (ownership !== "rent") return "";

        const commitment = finalNode?.pricing?.commitment;
        return commitment ? String(commitment) : "";
      },
      finalDeviceCardPriceHtml(res) {
        const pricing = res?.pricing;
        if (!pricing) return "";

        if (String(res?.ownership || "").toLowerCase() === "rent") {
          return this.finalMonthlyHtml(res);
        }

        const n = this.resolvePriceRef(pricing.devicePriceRef);
        if (typeof n !== "number") return "";

        return this.money(n);
      },

      canAddToCart(finalNode) {
        if (!finalNode || finalNode.type !== "final") return false;

        const ownership = String(finalNode.ownership || "").toLowerCase();
        const device = String(finalNode.device || "")
          .trim()
          .toLowerCase();

        if (!ownership) return false;
        if (!device || device.includes("monitored client")) return false;

        const programKey = this.resolvedProgramKey;
        const planKey = this.resolvedPlanKey;
        return !!(
          programKey &&
          planKey &&
          ownership &&
          device &&
          !device.includes("monitored client")
        );
      },
    },
  });

  app.mount("#quiz");
