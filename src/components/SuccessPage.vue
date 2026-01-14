<template>
  <div class="min-h-screen bg-gray-50 dark:bg-charcoal-800 flex items-center justify-center">
    <div class="max-w-md mx-auto p-8 bg-white dark:bg-charcoal-700 rounded-lg shadow-md text-center transition-colors duration-200">
      <div class="mb-6">
        <!-- Success Icon -->
        <div class="mx-auto flex items-center justify-center h-12 w-12 rounded-full bg-green-100 dark:bg-green-900 mb-4">
          <svg
            class="h-6 w-6 text-green-600 dark:text-green-400"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M5 13l4 4L19 7"
            ></path>
          </svg>
        </div>

        <h1 class="text-3xl font-bold text-gray-900 dark:text-white mb-2">
          Success!
        </h1>

        <p class="text-gray-600 dark:text-gray-300 mb-6">
          Your subscription has been processed successfully.
        </p>
      </div>

      <!-- Action Buttons -->
      <div class="space-y-3">
        <a
          href="/pages/index.html"
          class="w-full inline-block px-4 py-2 bg-gradient-to-r from-gray-800 to-black dark:from-gray-200 dark:to-white text-white dark:text-black rounded-lg hover:from-gray-900 hover:to-gray-800 dark:hover:from-white dark:hover:to-gray-100 transition duration-300 text-center shadow-md focus:outline-none focus:ring-2 focus:ring-gray-800 dark:focus:ring-gray-200 focus:ring-offset-2"
        >
          Back to Home
        </a>

        <p class="text-sm text-gray-500 dark:text-gray-400 mt-4">
          You can now use the Audify Extension in your Chrome browser.
        </p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'
import { trackEvent, ANALYTICS_EVENTS } from '@shared/utils/analytics'

const token = localStorage.getItem('access_token')

const handlePostSubscriptionTasks = async () => {
  if (!token) {
    return
  }

  try {
    // Handle post-subscription tasks
  } catch (error) {
    console.error('❌ Error in post-subscription tasks:', error)
  }
}


onMounted(() => {
  // Handle URL parameters (e.g., from Stripe)
  const urlParams = new URLSearchParams(window.location.search)
  const sessionId = urlParams.get('session_id')
  const paymentIntent = urlParams.get('payment_intent')

  // Track successful purchase
  trackEvent(ANALYTICS_EVENTS.CREDIT_PURCHASE_SUCCESS, {
    session_id: sessionId || 'unknown',
    payment_intent: paymentIntent || 'unknown',
  })

  if (sessionId) {
    // You could validate the session with your backend here
  }

  if (paymentIntent) {
  }

  handlePostSubscriptionTasks()
})
</script>